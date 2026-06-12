---
title: "Rsync command works in terminal, fails in crontab"
date: 2013-09-12
forum: Server Platforms
---

### Post by ChrisRChamberlain on 2013-09-12
Hi all

The command```
rsync -e ssh --protect-args -varuzP "chris@remotesite.com:/home/chris/Ubuntu One/MHbackup/" "/home/chris/Ubuntu One/MHbackup/" >> "/home/chris/Ubuntu One/MHbackup/rsynclog.log"
```works in the terminal, (Server 12.04), but fails in a crontab, code being```
@midnight rsync -e ssh --protect-args -varuzP "chris@remotesite.com:/home/chris/Ubuntu One/MHbackup/" "/home/chris/Ubuntu One/MHbackup/" >> "/home/chris/Ubuntu One/MHbackup/rsynclog.log"
```The error message from the crontab is>  ssh: connect to host remotesite.com port 22: Connection timed out
rsync: connection unexpectedly closed (0 bytes received so far) [Receiver]
rsync error: unexplained error (code 255) at io.c(605) [Receiver=3.0.9]So, perhaps the command is too long for the crontab?

TIA

---

### Post by nerdtron on 2013-09-12
Hmm.. If I were to do this, I'll create a script with that command.
```
#!/bin/bash
rsync -e ssh --protect-args -varuzP "chris@remotesite.com:/home/chris/Ubuntu One/MHbackup/" "/home/chris/Ubuntu One/MHbackup/" >> "/home/chris/Ubuntu One/MHbackup/rsynclog.log"
```

And save it to /path/script.sh
Then crontab I'll add a crontab entry.
```
0 0 * * * /path/scrpit.sh
```

And please check, can you ssh on "remotesite.com" passwordless?

---

### Post by ChrisRChamberlain on 2013-09-12
nerdtron

Thanks for your reply.

Anticipating such a suggestion, have already created a file 'rsyncbackup.sh" with code as:-
```
#!/bin/bash

echo " " >> "/home/chris/Ubuntu One/MHbackup/rsynclog.log"
echo "It's $(date)" >> "/home/chris/Ubuntu One/MHbackup/rsynclog.log"
echo " " >> "/home/chris/Ubuntu One/MHbackup/rsynclog.log"
rsync -e ssh --protect-args -varuzP "chris@remotesite.com:/home/chris/Ubuntu One/MHbackup/" "/home/chris/Ubuntu One/MHbackup/" >> "/home/chris/Ubuntu One/MHbackup/rsynclog.log"
```

Yet to try it, but, yes, passwordless login works in a terminal.

Curious as to what causes it to fail as a cronjob?

---

### Post by Lars Noodén on 2013-09-12
Are you using a key for authentication?  If so are you also using the agent to hold the key?   cron uses a different environment from the login shell and the variables SSH_AGENT_PID and  SSH_AUTH_SOCK need to be loaded specifically if they are to be used.  If the key is one of those somewhat dangerous "passwordless" keys you can get rsync to reference it directly.

```

rsync -e 'ssh -i /home/chrisrchamberlain/.ssh/some_rsa_key' -av ...

```

---

### Post by ChrisRChamberlain on 2013-09-13
Thanks to nerdtron and Lars Nooden for your contributions.

Running the command in a script resolves the issue.

Still feel the length of the command may be the problem - a shorter version worked in the past, the other difference then being the absence of the '--protect-args/' argument.

---

### Post by hawkmage on 2013-09-13
Two things to keep in mind when using cron to run things.  
1) The PATH variable may not be what you think it is.  Either validate the lath that is used or use the full path to executeables that are called.
2) Use a script that has the #!/bin/bash or what ever shell you are writing it for.  Cron may not run the same shell that you do.

---

