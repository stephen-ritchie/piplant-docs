# piplant-docs


## Starting PiPlant
```bash
ssh piplant@piplant.localdomain (password is 'piplant')

cd dev/piplant-server/
source venv/bin/activate
export FLASK_APP=piplant.app
export FLASK_ENV=production

# Start PiPlant. Not recommended if your SSH session will be terminated.
flask run --host=0.0.0.0 --port=5000

# (Recommended) Start PiPlant as a background process. Store the process's PID in a text file. Useful for killing the process later.
nohup flask run --host=0.0.0.0 --port=5000 > out.log 2>&1 &
echo $! > save_pid.txt

```

## Stopping PiPlant
If PiPlant was started as a background process, use the commands below to find the process ID (if you didn't save it to a text file) and 
kill the process. If not a background process then ```CTRL+C``` will stop the server.
```bash
# Get the process PID
ps -ef | grep "flask run"

# Stop PiPlant by killing its process
kill <PID>

```

## Updating
1. Stop PiPlant
2. From anywhere within `piplant-server` pull the most recent revision with `git pull`
3. Start PiPlant


## MongoDB
```bash
# Start MongoDB
sudo systemctl start mongod

# Verify MongoDB has started
sudo systemctl status mongod

# (Optional) Configure MongoDB to start on reboot
sudo systemctl enable mongod

# Stop MongoDB
sudo systemctl stop mongod

# Restart MongoDB
sudo systemctl restart mongod
```
