---
title: "Creating an &quot;ssh tunnel only&quot; user account"
date: 2007-03-15
forum: Server Platforms
---

### Post by RichardBronosky on 2007-03-15
I'd like to create a user account that is only good for creating an ssh tunnel.  I've tried to achieve this by putting different entries in passwd for the user's shell.  I tried writing a  bash script like this:
```

#!/bin/sh
sleep 5
exit

```

...and setting that as the shell, which seems to work of kicking the user off after 5 seconds (I intend to extend this sleep later) and does prevent the user from ever seeing a shell prompt.

The problem is this:  When I connect with "ssh -L 8080:videoserver:80 tunneluser@remhost" and then quickly launch vlc [http://127.0.0.1:8080/videofeed](http://127.0.0.1:8080/videofeed) the connection stays open until I close vlc... long after the 5 seconds.

What gives?  Is there a better way to do something like this? (I'm sure there must be)

Pleas advise.

---

### Post by SjRaptor on 2007-03-17
hmm, I'm having trouble understanding what you're trying to accomplish here. I don't see why you'd want to start an ssh session for 5 seconds and then exit?

and why not just set the shell to `/usr/sbin/nologin` if you don't want to allow the user to have a shell?

---

### Post by scxtt on 2007-03-17
i would imagine any "ESTABLISHED" connection will stay open until it's terminated ... i'd make sure that you CAN'T connect after 5 seconds have passed, then you'll know the connection is actually being terminated ...

---

### Post by RichardBronosky on 2007-03-17
> **SjRaptor said:**
> hmm, I'm having trouble understanding what you're trying to accomplish here. I don't see why you'd want to start an ssh session for 5 seconds and then exit?

and why not just set the shell to `/usr/sbin/nologin` if you don't want to allow the user to have a shell?

You are right, I didn't give much info.  Here is the situation.  In my baby nursery I have a network camera pointed toward the crib.  I want the grandparents to be able to look at the stream, but I'm not opening it up to the world.  The only way the view it is the create an ssh tunnel to my public facing firewall, like so:
```
ssh -L 8080:networkcamera.internaldomain:80 tunneluser@outward_facing_DNS_name.remote.host.com
```
Then launch vlc to connect to the local port that is being forwarded to the network camera inside my private network via SSH tunnel, like so:
```
vlc http://127.0.0.1:8080/videofeed
```

This is all fine and good.  I can write a script to do this and put it on their desktops.  The problem is, I don't want them connecting to the camera and then leaving it open for days or weeks at a time.  So, I'd like to find a way to kick them off after 20 minutes, regardless of what they are doing.  If they want to watch longer, they just reconnect.

For my testing purposes I set the sleep to 5 seconds, just so I didn't have to wait so long for each test.

As it is, that script I attached will indeed stop the ssh client from seeing a terminal, and disconnect after 5 seconds.  That is unless there is a vlc connection to the tunnel.  Then the SSH connection stays alive until vlc is closed.  This is of course undesirable and defeats the whole purpose.

Is there another route to take?  Maybe I should use the /usr/sbin/nologin as the shell, and use another process for doing the disconnection.  I'll have to see if /usr/sbin/nologin allows a connection for a tunnel, but no shell.  If by nologin, they mean noconnection, that is not the goal.

---

### Post by Crashmaxx on 2007-03-22
Try this:
```

#!/bin/sh
ssh -L 8080:networkcamera.internaldomain:80 tunneluser@outward_facing_DNS_name.remote.host.com
vlc http://127.0.0.1:8080/videofeed
sleep 5
killall vlc
exit

```
That has the login stuff and it kills the stream before exiting. That way there should be no process to wait for. There may be a more graceful way to kill it, but this will work at least.

---

### Post by Mr. C. on 2007-03-22
The system your grandparents are using is a PC ?

If so, instead of writing a script, install Tunnelier for them.  You configure the settings you want (like connect to the system, setup the tunnel, not to open a terminal, and launch a program).  You save the profile and just send them the updated profile when you want to make changes.  They just double click the profile which will connect, and open the desired program upon connect.

MrC

---

### Post by RichardBronosky on 2007-03-22
Guys I appreciate the suggestions.  I will definitely add Tunnelier to my process since the grandparents are on Windows.

The thing I don't like is the idea:  Linux can't protect itself from a client that stays connected longer than is desired, so we must put the responsibility on the Windows machine.

So, the task is:
1. Make Linux reliably end an ssh connection *N* seconds after it begins even if it has initiated a tunnel and the tunnel is actively transporting data.
* I think I can do this by adding logic to the script I am using as a login shell.  I can get the pid of the session on the server side and kill it after *N* seconds.
2. Make sure that under no circumstances can the user get a shell.
3. Make sure that under no circumstances can the user tunnel anywhere within my network other than where I have designated.

Keep in mind that to make this grandparent proof, I am providing a no passphrase ssh key for authentication.  AND I know it is going to be used on an non-maintained, non-virus scanned Windows machine.

---

### Post by RichardBronosky on 2007-03-23
Here is the solution I have come up with:
```

root:/home/tunneluser$ echo; cat .ssh/authorized_keys2 |sed 's/\(ssh-dss\).*/\1 ...pubkey here.../';echo

permitopen="networkcamera.internaldomain:80",no-agent-forwarding,no-X11-forwarding,no-pty,command="$HOME/bin/tempshell" ssh-dss ...pubkey here...

root:/home/tunneluser$ echo; cat bin/tempshell 

#!/bin/rbash
CONNECT_TIME=30
echo "Disconnecting in $CONNECT_TIME minutes."

SSHD_PID=$(ps|sort|awk '$1 ~ /^[0-9]+$/ {print $1; exit;}')
  # The pids are issued in ascending order,
  # the first pid issued is for the sshd of the conection,
  # and you want to awk to filter out the column headers

sleep $[CONNECT_TIME*60]
echo "Ending PID:$SSHD_PID"
kill $SSHD_PID

# vi:syn=sh


```

It boils down to this:

**In the authorized_keys2 file I get most of my safety:
[LIST=1]
[*]This restricts where the client is allowed to tunnel to...
[LIST][*]permitopen="networkcamera.internaldomain:80"[/LIST]
[*]This makes sure the user never gets a shell (even if the command wasn't set, they would not get a shell.)...
[LIST][*]no-pty[/LIST]
[*]This executes my logoff script when no matter what the client tries to do on connect...
[LIST][*]command="$HOME/bin/tempshell"[/LIST]
[/LIST]

**The script gives me the comfort of knowing that the grandparents won't ever "forget they left to door open".  It has the following features:
[LIST=1]
[*]The tempshell script reliably kills the pid $SSHD_PID in $CONNECT_TIME minutes (I edited it to multiply to get the seconds) even if the tunnel is in use.
[*]Trying to Ctrl-C from the client drops the connection.  It does not return a shell.
[*]If from the client someone did figure out how to drop to the shell, it's rbash.  See: man rbash
[/LIST]

The connecting client is Windows based.  I originally put 2 icons on their desktop.  One is a shortcut to "putty.exe -load babycam" (based on [this]("http://the.earth.li/~sgtatham/putty/0.53b/htmldoc/Chapter3.html#3.7.1")) that is labeled "babycam step 1".  The second is a shortcut to the vlc command I gave earlier and it is titled "babycam step 2".  I look forward to using [Tunnelier]("http://www.bitvise.com/tunnelier") to make it one step.  I hope it works.  It would be really cool if it could produce a single exe with the ssh_key embeded...  I'll let you know how it goes.

Thanks everyone!

---

### Post by Mr. C. on 2007-03-23
You came up with the solution I was typing in another window before dinner arrived.  Nice work.

I would move the tempshell to somewhere like /bin or /usr/local/bin and use a non-variable path (eg. /usr/local/bin/tempshell vs. $HOME/bin/tempshell

Your ps | sort...  script won't always work. PIDs wrap.

Bash already sets your parent's PID anyway; its $PPID.

For safety, also set 

shopt -s huponexit

I switched to using Tunnelier as I could save profiles on my end, and send them to other users.  They never had to configure anything.  Putty requires ridiculous registry entires.

MrC

---

### Post by RichardBronosky on 2007-03-23
@Mr. C,

Great advice on both points.

One thing to note is that adding nopty seems to make it impossible to ctrl-c out of the connection.  And, killing the $PPID from the server as root does not kill the tempshell.  It does kill the "sshd: tunneluser@notty" command, but not the "/bin/rbash /home/tunneluser/bin/tempshell" command.  Even killing the "sshd: tunneluser [priv]" command, which is owned by root, won't kill the tempshell.  You have to kill it directly.  If I resolve that, I'll feel much better.

---

### Post by Mr. C. on 2007-03-23
Thanks.

Right, with no controlling terminal (a pty), there are no tty control characters.  These are defined and implemented in the tty/pty driver itself.  

Sorry, my PPID test was done in an interactive shell; it will be incorrect in your case.  Use something like:

ps | grep rbash | awk '{print $1}'

MrC

---

### Post by padde0711 on 2008-03-03
Hint: there is 'pgrep' and 'pkill'

---

