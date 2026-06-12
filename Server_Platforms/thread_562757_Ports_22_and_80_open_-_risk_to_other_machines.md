---
title: "Ports 22 and 80 open - risk to other machines?"
date: 2007-09-29
forum: Server Platforms
---

### Post by jonbey on 2007-09-29
Hello,

I am still very new to computers in general, so this may seem silly, but I need to check! 

I have installed Ubuntu onto my old pc, to act as a web server (mostly to test sites before uploading to professionally hosted servers). I have opened ports 22 and 80 on my router, and installed openssh-server.

Anyway, I am not really concerned (at the moment) for my Linux machine, but I also have an Xp and a Vista machine attached to the same router. Is there any risk now to these machines? Or would there only be a risk if ssh was installed on these machines, and if a web server were installed?

Just need to be doubly sure. 

Cheers

Jon.

---

### Post by howlsmoving on 2007-09-29
I'm pretty new to linux, but I think I can answer your question.

If your router is anything like mine, you'll have to assign an ip address to the open ports (port forwarding).  So as long as you give your server a static ip within the network, then, assign it to those ports, there shouldn't be any extra vulnaribilities to your windows machines.

---

### Post by jonbey on 2007-09-29
That is good to hear. I did have to give a network address for the port. But, here's another question - how are network addresses assigned? I am sure I once had a problem whereby the network addresses for the 2 XP machines (at the time) switched. I remember setting up rules in ZoneAlarm firewall to allow the two machine to connect, but the following  day they could not connect. When I took a look, then the IP's had changed, in the etc.etc.etc.1 became etc.etc.etc.2 

If this was to somehow happen again, would I then be at risk? 
How get I ensure that this does not happen. If it does, then the server will not run. Maybe it was a very odd one off issue?

---

### Post by MJN on 2007-09-29
Most(?) routers allow you to create a static client list whereby you can specify the MAC address of individual machines and permanently reserve an IP address for them to stop them getting a random/different address each time they connect.

To find the MAC address of a machine's NIC run 'ipconfig /all' (Windows) or 'ifconfig' (Linux). The address will be 6-bytes long written in hex, e.g. 00:AB:09:10:EB:AA.

You would normally assign an IP address that is outside of the pool of DHCP addresses, and indeed would only usually do this for servers which have specific services forward to them. Clients, on the other hand, can be left obtaining random addresses as they will never take on an address that has been reserved as above.

Mathew

---

### Post by steve.horsley on 2007-09-30
The biggest risk to your other boxes is probably a weak password on the Ubuntu box. There are bots out there that look for SSH servers and spend all day every day guessing usernames and passwords.

---

### Post by HermanAB on 2007-09-30
Yup, you have to ensure that you use a random password of at least 9 characters for *every* account on the Linux box (Common brute force dictionaries go up to 8 characters).

If you use a 4 character password, then your machine won't live very long...

You should also consider changing the SSH server configuration so it runs on a different port (eg 22222), to throw the script kiddies off (/etc/ssh/sshd_config).  Otherwise you may find that your machine slows down periodically as it gets hammered with bazzilions of password guess attempts.  Changing the port works remarkably well, since most script kiddies are stupid.

Cheers,

H.

---

### Post by nowshining on 2007-10-05
"Yup, you have to ensure that you use a random password of at least 9 characters for *every* account on the Linux box (Common brute force dictionaries go up to 8 characters).

If you use a 4 character password, then your machine won't live very long..."

I use 15 random characters as my login password - i don't do servers but that was some good info. you said there and i've learned a thing from ur post. :)

---

### Post by netlogic on 2007-10-05
Never use a password.
use a ssh key and strong passphrase.

---

### Post by nahham on 2007-10-05
A paraphrase and public/private key combination works quite well with SSH.  Here is a good [[COLOR=SandyBrown]_HOWTO_[/COLOR] ]("http://ubuntuforums.org/showthread.php?t=383053&highlight=putty") to show you how to do it and a bit more (connecting through any computer with your USB drive, which I found very useful when traveling).  

Another thing to watch for is making sure your ISP is not blocking the port you want to move your SSH to.

Finally, welcome to Linux .. (you are about to be amazed)..

---

