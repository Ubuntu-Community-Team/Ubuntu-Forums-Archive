---
title: "ssh command before connection termination"
date: 2015-02-17
forum: Security
---

### Post by sam116 on 2015-02-17
Hi Folks,
I am no really sure if this is the right place to post this, but here is my question. So I am "playing" Wargames on overthewire.org. Level 26 in the Bandit game requires you to log in through an ssh with RSA key. As soon as you log in, it kicks you out after displaying the contents of a text file. Is there a way to send a command to the shell before it executes the script that kicks you out? I managed to send command with the ssh -f and also -t command, which using the -v option appear as debug messages (command sent: pwd for example). However, there is no response to the command. How can I figure out what shell I am connecting to, and what is being executed.  
I know from a description online, that passwd contains a hint to what is being executed, but when I start the connection in this way

**********:~$ ssh -v -f -i pw26.txt bandit.labs.overthewire.org -l bandit26 grep bandit26 /etc/passwd

I get a lot of debug messages and this

debug1: Sending command: grep bandit26 /etc/passwd
::::::::::::::
/home/bandit26/text.txt
::::::::::::::
  _                            _ _ _   ___   __  
 | |                           | (_) | |__ \ / /  
 | |__   __ _ _ __   __| |_| |_   ) / /_  
 | '_ \ / _` | '_ \ / _` | | __| / / '_ \ 
 | |_) | (_| | | | | (_| | | |_ / /| (_) |
 |_.__/ \__,_|_| |_|\__,_|_|\__|____\___/ 
debug1: client_input_channel_req: channel 0 rtype exit-status reply 0
debug1: channel 0: free: client-session, nchannels 1
Transferred: sent 2360, received 2824 bytes, in 0.2 seconds
Bytes per second: sent 10309.2, received 12336.1
debug1: Exit status 0


Any hints? This is really bugging me

---

### Post by TheFu on 2015-02-17
Probably not.  They replaced the shell with something that runs that command, if they are smart.
OTOH, you might be able to cntl-c at just the right place if they aren't trapping interrupts.

Can't talk any more than this in these forums. Hacking or helping is against forums rules, even ethical hacking. Better try asking somewhere else.

---

### Post by cariboo on 2015-02-17
+1 to TheFu's post, we don't support this type of activity here. Thread closed.

---

