---
title: "Setting up Post fix with POP3 and SMTP"
date: 2010-10-19
forum: Server Platforms
---

### Post by kin37ik on 2010-10-19
g'day, im having trouble getting the config right for PostFix on my ubuntu server box, ive got the apt installed, but i cant figure out how to set everything up that that i can add new user accounts if they want to use a mail service, be able to send mail from any client that is setup correctly and and receive mail too their client, ive dabbled around and for the life of me cant work it out, im wanting to send mail out not just to users on a LAN network but plan to be using it on the net as well at some stage, help would be rgeatly appreaciated, cheers.

(also, i did look at the online documentation, but it's still not working, despite going through a couple of pages.

---

### Post by HermanAB on 2010-10-19
Howdy,

Installing postfix, dovecot, apache and roundcube is a good way to learn, but if you just want something that works for hundreds of users in about 20 minutes flat, then you need to install Citadel.

---

### Post by kin37ik on 2010-10-19
well i need something that is secure but can also host many accounts, ill give the top one a go and report back if i have any problems, cheers.

---

### Post by kin37ik on 2010-10-19
im now trying to install roundcube but the console just keeps telling me it's an unknown command

---

### Post by James78 on 2010-10-19
I use Webmin for this stuff. It sets up your services and everything right off from the start, then you just do a LOT of tweaking to make it work for your particular situation.

P.S. Sending mail (using a mail server) from a dynamic IP is a very bad idea.
Regardless though.. See [http://ubuntuforums.org/showthread.php?t=412410](http://ubuntuforums.org/showthread.php?t=412410)

---

### Post by kin37ik on 2010-10-19
right, finally got rouncube and stuff to install, unfortunately the login doesnt work :S so i think i havent git any user information on the database meybe?
 
 @james78: it wont be dynamic once everything is up and running properly


@herman: ive read a few posts and people say that Citadel isnt very secure, but is very scalable in the way of lots of users

---

### Post by James78 on 2010-10-19
> **kin37ik said:**
> @james78: it wont be dynamic once everything is up and running properly
Good good. :)

---

### Post by kin37ik on 2010-10-19
right, so i gave citadel a go instead of having to mess around with a bunch of settings to get it to work, and form what little documentation i could find, your supposed to be able to log into it by using firefox or something else, but i cant do that :S so what am i supposed to do once it's installed?

---

### Post by HermanAB on 2010-10-20
Just go to the citadel.org web site.  The support web site is actually a Citadel system that has been going for the past 20 years or so.

You can use any browser you like to connect to Webcit, even the Lynx or Links text browsers. 

There are also Citadel howtos on my web site.

---

