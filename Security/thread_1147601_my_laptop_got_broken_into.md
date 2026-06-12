---
title: "my laptop got broken into???"
date: 2009-05-03
forum: Security
---

### Post by jamescoleman on 2009-05-03
So I was in the basement working on the ssh problem I'm having until I used the finger command on my laptop to find out that someone was logged in from 115.127.0.13*
which finds out a website from bangladash for news. I see that they've been logged into for 4 hours. I later goto my desktop and login using putty to see that they're still in. I nmap my lo back interface to find this... 

root@user-laptop:/# nmap 127.0.0.1

Starting Nmap 4.76 ( [http://nmap.org](http://nmap.org) ) at 2009-05-03 16:00 EDT
Interesting ports on localhost (127.0.0.1):
Not shown: 987 closed ports
PORT     STATE SERVICE
22/tcp   open  ssh
25/tcp   open  smtp
80/tcp   open  http
110/tcp  open  pop3
143/tcp  open  imap
465/tcp  open  smtps
587/tcp  open  submission
631/tcp  open  ipp
993/tcp  open  imaps
995/tcp  open  pop3s
2020/tcp open  xinupageserver
5222/tcp open  unknown
5900/tcp open  vnc

I only had 22/80/5900 open to start with. 

Then I run over to check the auth log file to find that the person from the same
ip address starts to use some program to find the correct user name and password.
Does anyone know what type of program does this and some possible names of it? 

I checked out what port 2020 is and I found out that it's some rootkit. 
Does anyone know what programs that I can use to scan for rootkits on my laptop?

I also guess a few groups got added which are arpwatch and citadel and 
I guess the services aren't anything to worry about unless the person comes
back and uses them?? 

This is mostly myfault because I used an easy password along with an easy
user name.  Plus I have port 22 open. If this happens again is there anyway to 
close that persons connection to my computer? Also does anyone have any tips
on shutting down the ports but the ones I opened to start with?

---

### Post by bodhi.zazen on 2009-05-03
Well, I suggest you read the sticky at the top of these forums re: security.

You can restrict access in a variety of ways from iptables (firewall) to better passwords to proper configuration of you servers to apparmor.

---

### Post by HermanAB on 2009-05-03
Hmm, Ubuntu is secure out of the box.  If it gets broken into, it is due to something you installed yourself.  I have noticed many threads with people complaining about getting hacked, but you are the first person that actually did a scan to see why.

I think that the culprit is VNC.  You should not run VNC on an exposed machine.  Use SSH instead, since it can do everything that VNC does and it is secure.

Finally, always use looooong passwords for all accounts.  All the hacked machines I have repaired over the years, had some wise guy who thought that a 4 character password was cool.

---

