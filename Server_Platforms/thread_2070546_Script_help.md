---
title: "Script help"
date: 2012-10-13
forum: Server Platforms
---

### Post by chadk5utc on 2012-10-13
Good morning,
I find myself having to do several things repeatedly(across @400 machines this time) and would Love to automate this task as much as possible. The following is a list
Note: this will need to be done by ip address
1. Logon as root
2. copy an existing script from my pc to the root of another
3. change permissions of this script
4. Execute said script

Not asking to much is it..... Hahaha Seriously though any help Greatly appreciated.

Chad

---

### Post by ian dobson on 2012-10-13
Hi,

Maybe have a look at using ssh/expect, something like this:-

```

#!/bin/bash
HOST="localhost"
USER="myuname"
PASS="mypassword"

VAR=$(expect -c "
spawn ssh $USER@$HOST
expect \"password:\"
send \"$PASS\r\"
expect \"\\\\$\"
send \"ls\r\"
expect -re \"$USER.*\"
send \"logout\"
")

echo "==============="
echo "$VAR"

```

Maybe just make two scripts, the one above and the second that calls this script with ip address/password as parameter.

On my servers I have a script in rc.local that checks if updates are on the update server (local to network) and calls the attached script if necessary.

Regards
Ian Dobson

---

### Post by Lars Noodén on 2012-10-13
I would use keys, with a good strong passphrase, for authentication and disable password log in.  

Then when preparing to work with the 400 or so computers, load the key first into the agent using [ssh-add](http://manpages.ubuntu.com/manpages/precise/en/man1/ssh-add.1.html).   Then you can automate the transfer and execution of the script.

```

scp -i /path/key_rsa /path/to/script.sh root@$HOST:/tmp/
ssh -i /path/key_rsa root@$HOST /tmp/script.sh

```

I'm pretty sure that the script will carry over its permissions in the copy.

---

### Post by thnewguy on 2012-10-13
Forgive me, but if you need to do this exact same series of steps for around 400 computers I feel you are doing it backward. Instead of having your local machine send a script to these machines, why not have the machines download the script from you?

Assuming you have OpenSSH server running on your local machine (or if you have a server anywhere that you feel can host the script) you could put a crontab on your 400 machines that looks like this:

```

#!/bin/bash

# wait for a random period of time no more than one hour
sleep_time=$(($RANDOM % 3600))
sleep $sleep_time

# save the previous script used
mv command_script command_script-backup
# download new script
scp your-hostname:scriscript_name command_script

# don't run it if the script is hasn't changed
cmp command_script command_script-backup && exit 1

chmod 755 command_script
./command_script


```

Then enable a cron job to run the script for you as root once every hour/day/week. Just make sure that the remote machines
1) Have the script installed
2) Have the proper crontab entry
3) Have permission to access your machine or the server where the new script will be.

---

### Post by chadk5utc on 2012-10-13
Hi and thanks for the replies. I will at some point setup a dedicated updates server for doing this as it will be much easier. Im all for working smarter not harder. Ive taken this challenge on myself as some of the others I work with would sooner do it all by hand one at a time, I think it foolish as we all have tons of other things/projects to take care of. Once in place the script being sent will backup several things on remote machines across the country then we have to retrieve and store these files on yet another remote system. Thanks again for the replies I will gladly take any and all suggestions.

 Chad

---

