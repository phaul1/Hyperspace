# HyperSpace CLI Node Setup Guide

## 1️⃣ Install HyperSpace
Run the following command to install HyperSpace:
```bash
curl https://download.hyper.space/api/install | bash
source /root/.bashrc
```

## 2️⃣ Start Your Node
Run HyperSpace inside a `screen` session so it continues running in the background:
```bash
screen -S hyperspace
```
Now, start the node:
```bash
aios-cli start
```
Detach from the screen using:
```
CTRL + A + D
```
Your node must be up before you begin configurations. To verify your node is running use:
```bash
ps aux | grep aios
```
You should see 3 line items. Restart if you dont
```bash
screen -r hyperspace
aios-cli stop
aios-cli kill
aios-cli start
```
Detach from screen & verify again

## 3️⃣ Configure Your Node
### Download the Required Model
```bash
aio-cli models add hf:second-state/Qwen1.5-1.8B-Chat-GGUF:Qwen1.5-1.8B-Chat-Q4_K_M.gguf
```
### Import Your Private Key
To obtain your private key go to https://node.hyper.space/
Click the `key logo` next to `public key`
Click `COPY CURRENT PRIVATE KEY` under `Export key`

Create a `.pem` file and paste your private key:
```bash
nano pem
```
After pasting your pkey use `CTRL+X`, then `Y`, then `ENTER` to save it. Now import your key into Hyperspace node using:
```bash
aio-cli hive import-keys ./my.pem
```
### Login using:
```bash
aio-cli hive login
```
### Make Sure the Model is Registered
```bash
aio-cli hive connect
```

### Select Node Tier
To maximize rewards, set your tier:
```bash
aio-cli hive select-tier 3
```

## 4️⃣ Useful Commands
### Start, Login, and Connect in One Command
```bash
screen -r hyperspace
aio-cli start --connect
```
### Version check
```bash
aio-cli version
```
### Check Your Points
```bash
aio-cli hive points
```
### Stop Node
```bash
aio-cli kill
```

## 5️⃣ Removal Commands
If you need to remove everything related to HyperSpace, run the following commands:
```bash
aios-cli kill
rm -rf ~/.aios
rm -rf /root/.aios
rm -f pem
rm -f /usr/local/bin/aios-cli
```
This will stop the node, remove its configuration, and delete all associated files.
