---
title: "How common are SSH attacks"
date: 2009-07-21
forum: Security
---

### Post by R.Bucky on 2009-07-21
I have ssh installed on my desktop box so that I can remote into it and then into my server. My logs are full of ip's trying to gain access with random user names. They are hitting my box about 4 times a minute from various ip's around the world (e.g. china, Texas, you name it). How much of these attacks are normal and would it be wiser to simply forward ssh queries to my Ubuntu Server box versus my GUI "daily driver?"

---

### Post by squaregoldfish on 2009-07-21
That sounds like a roughly normal level of login attempts on a standard SSH setup. Assuming you haven't been hacked, then all is well and good - SSH is standing up to the attempts so far.

If, like me, you'd rather not have anyone trying to get in at all, you can simply move your SSH server to a port other than the standard (22) - somewhere above 10000 will do the job nicely. I've not had a single login attempt since I did this more than a year ago.

Steve.

---

### Post by TuckLive on 2009-07-21
> **squaregoldfish said:**
> That sounds like a roughly normal level of login attempts on a standard SSH setup. Assuming you haven't been hacked, then all is well and good - SSH is standing up to the attempts so far.

If, like me, you'd rather not have anyone trying to get in at all, you can simply move your SSH server to a port other than the standard (22) - somewhere above 10000 will do the job nicely. I've not had a single login attempt since I did this more than a year ago.

Steve.

+1

Going through pages and pages of login attempts is not fun and gets old fast.

---

### Post by R.Bucky on 2009-07-21
Ok - no, i have not been hacked. I have a password of steel that even I cannot remember at times. Changing to a non-standard port is the best advice. Thank you for the input.

---

### Post by .nedberg on 2009-07-21
> **squaregoldfish said:**
> That sounds like a roughly normal level of login attempts on a standard SSH setup. Assuming you haven't been hacked, then all is well and good - SSH is standing up to the attempts so far.

If, like me, you'd rather not have anyone trying to get in at all, you can simply move your SSH server to a port other than the standard (22) - somewhere above 10000 will do the job nicely. I've not had a single login attempt since I did this more than a year ago.

Steve.

+1

I also use fail2ban, but it is not much use if you change port.

---

### Post by HermanAB on 2009-07-21
These attacks happen all the time.  A non-standard port will throw them off.  You can also limit login to specific IP addresses in /etc/hosts.allow

---

### Post by bodhi.zazen on 2009-07-21
Nothing like reading the logs to generate a little paranoia :twisted:

If you secure your ssh server you should be fine. Some people go no further then that.

[AdvancedOpenSSH - Community Ubuntu Documentation]("https://help.ubuntu.com/community/AdvancedOpenSSH") 

If you want to go beyond that, change the default port, use iptables, denyhosts, or fail2ban.

Or something more robust such as ossec.

Personally I user the default port + keys + iptables . Simple to set up, uses the default applications, (so nothing to add), portable across distros, and quite secure.

Up to you.

---

### Post by Dave_Connor on 2009-07-21
I changed the default port on my system to avoid auth.log getting filled up. Key auth is VERY secure and works much better then password auth. But changing the port number and a secure password will work enough to kick off a large number of brute-bots.

---

### Post by hackertarget on 2009-07-21
My 2c

1. As mentioned above - move SSH to another port (Change the Port directive in /etc/ssh/sshd_config).

2. Install [ossec]("http://www.ossec.net"), spend 20 mins configuring and now have a box that will notify you if anything "weird" starts to happen on your box. If you start getting failed access attempts on ssh running on a high random port, it is likely an indication of a targeted attack rather than a bot on port 22.

3. SSH Keys - are great but caution is required if you are running keys with no passwords. If you have a bunch of boxes and your key gets compromised - the attacker now has access to all your boxes.

---

### Post by lensman3 on 2009-07-21
Using iptables just block IP numbers from Africa, Asia, South America, and whatever country you don't want a hacker trying from.  Only allow IP's from  approved countries.  Also block the 10.x.x.x, 192.168.x.x and the 172.?.x.x (Class B).  That cuts down a huge number of attacks.

---

### Post by synapsys on 2009-07-21
I agree with port obscurity... port scanners only scan a limited range of ports unless specifically told otherwise. If a hacker is determined, he will get in, I don't care how 'secure' your password is. From what it sounds like, nobody is targeting you specifically, so changing the port number should do nicely.

---

### Post by kevdog on 2009-07-22
Hmmm -- if you are using a 4096 bit RSA key I might beg to differ with the statement someone will get in -- I suppose that might be true but it would be years if not longer.

---

### Post by dragos2 on 2009-07-22
Change the default sshd port from 22 to something higher not defaulty covered by nmap
and/or bots, of course you can do an nmap host -p1-65535 but few bots do that in order to detect your sshd installation for the simple fact that they create too much noise and attract
consequences.

Except that in Ubuntu 8.10 and later if I am not wrong there is a port limit feature in ufw
ufw limit 22.

Except that you can check the logs carefully.

---

### Post by The Cog on 2009-07-22
I have mine set up with iptables only allowing SSH in from 3 places: Local LAN, work and OpenVPN network.

So I can connect directly with SSH from home or work, and from anywhere else I have to connect with OpenVPN and then I can connect with SSH. I like OpenVPN - it's not easy for an attacker to find, let alone to brute-force. And I keep my OpenVPN key in an encrypted folder.

---

### Post by JK3mp on 2009-07-22
Unless there specifically targeting you for a reason or thus you contain sensitive information on your computer, than changing the port to something higher that is not the default for common software should due fine. And as stated earlier, a good password along with encryption should make it impossible(in terms that they don't have a super computer and/or wanna wait years to get your pass, usually they'll just try something else) for them to get in, just stay updated, ssh exploits are'nt around too often, but Bruteforce/Dictionary attacks are, which again with a strong password would be rendered useless.

---

### Post by bodhi.zazen on 2009-07-22
> **dragos2 said:**
> change the default sshd port from 22 to something higher not defaulty covered by nmap
and/or bots, of course you can do an nmap host -p1-65535 but few bots do that in order to detect your sshd installation for the simple fact that they create too much noise and attract
consequences.

+1

---

