<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Account Dashboard</title>
    <style>
        body { font-family: Arial, sans-serif; padding: 20px; background: #f4f4f4; }
        h1 { color: #333; text-align: center; }
        textarea { width: 100%; height: 100px; margin-bottom: 10px; }
        button { padding: 10px 20px; background: #007bff; color: white; border: none; cursor: pointer; margin-bottom: 10px; }
        button:hover { background: #0056b3; }
        table { width: 100%; border-collapse: collapse; margin-top: 20px; }
        th, td { border: 1px solid #ccc; padding: 10px; text-align: center; }
        th { background-color: #007bff; color: white; }
        td button { background-color: #28a745; }
        td button:hover { background-color: #1e7e34; }
        #logo { width: 50px; cursor: pointer; margin-bottom: 20px; display: block; margin-left: auto; margin-right: auto; }
    </style>
</head>
<body>

    <h1>Account Dashboard</h1>
    <img id="logo" src="https://upload.wikimedia.org/wikipedia/commons/a/ab/Logo_TV_2015.png" alt="Start Logo" title="Click to Start All">
    
    <textarea id="accountInput" placeholder="Paste accounts here, one per line..."></textarea><br>
    <button onclick="loadAccounts()">Load Accounts</button>

    <table id="accountTable">
        <thead>
            <tr>
                <th>Account</th>
                <th>Action</th>
            </tr>
        </thead>
        <tbody>
            <!-- Accounts will appear here -->
        </tbody>
    </table>

    <script>
        const tableBody = document.querySelector("#accountTable tbody");

        function loadAccounts() {
            tableBody.innerHTML = "";
            const accounts = document.getElementById('accountInput').value.split('\n').filter(a => a.trim() !== "");
            accounts.forEach(acc => {
                const row = document.createElement('tr');
                row.innerHTML = `<td>${acc}</td><td><button onclick="startAccount('${acc}')">Start</button></td>`;
                tableBody.appendChild(row);
            });
        }

        function startAccount(account) {
            alert(`Started action for account: ${account}`);
            // Here you can add any real action per account
        }

        // Clicking the logo triggers all accounts
        document.getElementById('logo').addEventListener('click', () => {
            const accounts = document.getElementById('accountInput').value.split('\n').filter(a => a.trim() !== "");
            accounts.forEach(acc => startAccount(acc));
        });
    </script>
</body>
</html>
