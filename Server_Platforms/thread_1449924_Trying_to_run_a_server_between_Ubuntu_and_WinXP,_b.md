---
title: "Trying to run a server between Ubuntu and WinXP, but..."
date: 2010-04-08
forum: Server Platforms
---

### Post by sotvomike on 2010-04-08
......none show up on the network. They are both connected hardwire to my router. When I open the admin page to my router, I see everything connected on there just fine. When I go to Network Places in XP, I see nothing. When I run Remote Desktop or Terminal Server Client or anything else on Ubuntu, even when I put in the IP of the other computer, it cannot see it. I am running TightVNC on the XP machine in Listening Mode and still Ubuntu could not see it. I'm figuring if neither computer shows on each other's network, naturally they won't be able to connect. I am running Windows Firewall on SP3 on the XP machine. Every search I've run on this problem people can see their computers just fine but can't connect. I can't even see the computers. What am I doing wrong?

---

### Post by cdenley on 2010-04-08
I can't help you with your windows firewall. What servers did you install in ubuntu? It does not have any server software pre-installed, of course, so you should not "see" ubuntu from windows unless you installed a server.
```

sudo netstat -tlnp

```
What are the IP addresses of each computer?

---

### Post by sotvomike on 2010-04-08
I am at work right now so I will post the results later tonite.  As far as Server software, I had TightVNC installed in Ubuntu as well.  When it would scan for other computers, it found nothing even though the XP box is running TightVNC as well in Listening mode.  Anyways, I'll post the results tonite.

---

### Post by BobVila on 2010-04-08
start -> run -> services.msc

Disable windows firewall and give it another go. If that works, re-enable it and add exceptions.

Can you ping each machine from the other? SSH via Putty from the WinXp box to your ubuntu machine?

---

### Post by cdenley on 2010-04-08
> **sotvomike said:**
> I am at work right now so I will post the results later tonite.  As far as Server software, I had TightVNC installed in Ubuntu as well.  When it would scan for other computers, it found nothing even though the XP box is running TightVNC as well in Listening mode.  Anyways, I'll post the results tonite.

As I said, I'm not sure how to help you configure your windows firewall. I was asking about servers on your ubuntu computer. There are none by default, so what servers did you install since you expect to "see" the ubuntu computer from windows.

---

### Post by sotvomike on 2010-04-08
Thanks for the leads, guys!  Will try all your suggestions when I get home and post the results.

---

### Post by BobVila on 2010-04-08
> **cdenley said:**
> As I said, I'm not sure how to help you configure your windows firewall. I was asking about servers on your ubuntu computer. There are none by default, so what servers did you install since you expect to "see" the ubuntu computer from windows.

Just to clarify this comment - you'll only see the Ubuntu machine in Windows' Network Places if you've installed Samba on the ubuntu box.

---

### Post by sotvomike on 2010-04-08
Yes, Samba is installed in the Ubuntu box, with SWAT installed as well.  samba.conf is edited to change WORKGROUP to MSHOME. Still does not see the XP in either WORKGROUP or MSHOME.  And when starting the Samba GUI, it cannot see XP.

---

### Post by cdenley on 2010-04-08
> **sotvomike said:**
> Yes, Samba is installed in the Ubuntu box, with SWAT installed as well.  samba.conf is edited to change WORKGROUP to MSHOME. Still does not see the XP in either WORKGROUP or MSHOME.  And when starting the Samba GUI, it cannot see XP.

Places>Connect to Server...

If you can't connect to your windows server from ubuntu (by IP address), that is probably a windows problem. Perhaps your firewall is blocking it. Run this command from ubuntu, substituting the IP address of your windows computer.
```

nc -z -v -w 5 windowsip 139

```
If that says "open", then you should be able to connect. If it says "failed" or "timed out" or something, it is being firewalled.

---

### Post by sotvomike on 2010-04-08
Thanks!  So much help!  Can't wait to get home and try this all.  Been up late for 2 days trying to figure it out.  Would be nice to finally solve it and get some sleep!  :)

---

### Post by Ryan Dwyer on 2010-04-08
sudo apt-get install winbind

---

### Post by sotvomike on 2010-04-08
Ok, I already have winbind installed and is the current version.

Here is terminal result: nc -z -v -w 5 xxx.xxx.x.xxx 139
xxx.xxx.x.xxx: inverse host lookup failed: Unknown host
(UNKNOWN) [192.168.0.167] 139 (netbios-ssn) open 

I killed the Firewall service and still nothing.  Under My Network Places, Local Network in XP, it just lists my router (which opens the admin page when I click it).

In Places, when I click NETWORK, I see WINDOWSNETWORK.  I click it and it says Failed to Mount Location. Failed to retrieve share list from server.

"Places>Connect to Server...

If you can't connect to your windows server from ubuntu (by IP address), that is probably a windows problem."

When I do that, I can see the folders and drives in XP!  Yay!  But it is asking for user name and password to access.  I have my username and domain already filled in, but all passwords I enter are wrong. Which user and pass am I supposed to use?

---

### Post by cdenley on 2010-04-08
> **sotvomike said:**
> When I do that, I can see the folders and drives in XP!  Yay!  But it is asking for user name and password to access.  I have my username and domain already filled in, but all passwords I enter are wrong. Which user and pass am I supposed to use?

Your windows password I would assume. That is a windows question.

---

### Post by sotvomike on 2010-04-09
I assumed that as well, but we never set a password to login, to automatically log in each time. And that was 5+ years ago.   Hmmm, new set of problems now.

OK!  So I finally connected to the XP computer thru Terminal Server Client.  It is through VNC that it is connected.  NOw, almost to the end!  I want to transfer files from my Ubuntu box to the XP box, but it doesn't quite let me.  Is it something simple that I'm missing?

---

