---
title: "SSH attack appeared after adding Win7 to the network"
date: 2010-11-27
forum: Server Platforms
---

### Post by TDrakeHI on 2010-11-27
Don't know if this is relevant or if I should take this info to another board, but I figured I would start here as this is the platform that it occured on.

Running Ubuntu 10.04 LTS Server running as a PDC for a Win client network.  All my clients up to today have been WinXP and have been running with only mild hiccups since the initial installation in Aug '09.  We recently purchased a new Dell Vostro 230 to replace an ailing machine and Dell forced Win7 on us.  We got the V.230 with the backup of being able to load Ubuntu 10.10 and run the necessary software on WinXP through VirtualBox, if Win7 proved to be incompatible with our network setup.  We could not get Win7 to go through the authentication procedure and in the process of going through the auth.log file, I noticed a strange occurence.  I was under attack.  The log was flooded with  sshd auth failures all coming from the same UK IP address.  I kept searching back through the log and found out that the attack had started shortly after we plugged in and started up the Win7 machine for the first time.  Now, I have a hard time believing in coincidence, but I will admit that coincidence is a possibility.  Once I figured out what was going on, I shut down the ssh server until I could figure out a better solution. 
 
So, here goes with the ?'s I have.  
(1)Is it possible that the Win7 machine might have brought some roving hacker to my IP doorstep or am I just Microsloth paranoid?  
(2)Is there a way that I can block offsite ssh access to all but myself or other authorized computers using a firewall or some other defense mechanism.  
(3)Is there a way to setup the system so that a number of auth failures will set off some sort of warning, either by email or SMS or something so that I can be made aware of this in the future?  
(4)Has anybody else heard of something similar happening?

This was a wake up call to me, and even though no sensitive customer data is currently stored in my network, I want to be able to have the peace of mind that the network is secure.  

TDrakeHI

---

### Post by James78 on 2010-11-27
1. No, most attackers are zombie computers that scan IP ranges day by day, and try to hack computers that reply to their probes (adding another zombie computer to their botnet that then tries to hack other computers, making more and more infected computers. You don't want your PC to be used this way).
2. You can probably do that (check the links I posted). What you should also do is disable passworded logins, make sure the root account in Ubuntu is disabled (should be disabled by default), disable root account login in SSH, and enable only keyed logins.
3. Absolutely! fail2ban specializes in this! :)
4. Have we?! Regular servers connected to the internet can get anywhere from 1, 2, or 20 hack attempts PER day!

Some extra addon inforation: You don't need passworded logins because that only allows the hackers a way to try to bruteforce there way in. But if you use key authentication ONLY, then they don't have your keys, and can never get in. They'll never have any hope of even trying to guess anything. Try it. Disable passworded logins, enable keyed logins, and try to connect. You get denied immediately if you aren't authorized.

Oh, and Windows has nothing to do with it. If your server is private, and you don't want anyone accessing it, you can do a few things. You can make sure it is completely not accessible from the internet at all. Or if you need it to face the internet, you can either make sure port 22 isn't accessible from the internet, or just change the SSH port from 22 to something else (cuts down attacks 10 fold in and off itself). Me, I elected to do none of these. I simply disabled root logins, passworded logins, enabled keyed logins, and use fail2ban. Works perfect for me!

[https://help.ubuntu.com/community/SSH](https://help.ubuntu.com/community/SSH)
[https://help.ubuntu.com/community/SSH/OpenSSH/Configuring](https://help.ubuntu.com/community/SSH/OpenSSH/Configuring)
[https://help.ubuntu.com/community/SSH/OpenSSH/Keys](https://help.ubuntu.com/community/SSH/OpenSSH/Keys)

---

### Post by R.Bucky on 2010-11-27
First off, change your SSH protocol to a non-standard port. I have had MAYBE a half dozen attempts in the last year on my non-standard ssh port, versus the hundreds per day on port 22. This is very simple to do and worth the 5 minutes to change the port and the port forwarding on the router.

As James78 said, Fail2Ban is awesome. I did a quick write-up on securing ssh here [[http://nwlinux.com/blog/securing-ssh-on-your-server/]("http://nwlinux.com/blog/securing-ssh-on-your-server/")].

---

### Post by windependence on 2010-11-27
IMHO it's not even worth trying to block this stuff, you'll drive yourself nuts. There ARE things you can do such as using very complex passwords, disallowing root logins via ssh, etc. They aren't getting in, so don't worry about it. You should also be running a good firewall separate from your box where you can trap that traffic if you wish. Running only a firewall on your backend box is not a good idea as you can still be taken down by too many request flooding your machine and comsuming all your CPU and memory. Stop the traffic before it gets to the box.
 
-Tim

---

### Post by R.Bucky on 2010-11-27
e.g. Soekris hardware firewall [http://nwlinux.com/blog/soerkis-pfsense-firewall/]("http://nwlinux.com/blog/soerkis-pfsense-firewall/")

---

### Post by czr114 on 2010-11-27
This has nothing to do with the Win7 machines as evidenced by the IP in the logs. It's nuisance-level background probing by compromised/botted systems.

If you're following good security practices, these are nothing but a nuisance line in the logs.

With either a properly strong password, or better yet, private key authentication, you have nothing to worry about.

If you want to decrease the cruft in the logs, then change the port.

Until the world is cleansed of tens of millions of compromised systems, this nuisance is not going to go away. Reporting them is a waste of time, as is setting up security alerts for something which: (1) won't quit, and (2) is incapable of breaking good security.

If you have users you suspect have horrendously weak passwords, then a ratelimit or failure-based IP bans would make sense. If your passwords are strong, or you're using private key authentication, there's no point in setting that up, since these automated probers have neither the endurance nor the time to break strong authentication.

You can learn about private key authentication here:

[http://www.debian-administration.org/articles/530](http://www.debian-administration.org/articles/530)


Ubuntu's Passwords and Encryption Keys tool (aka Seahorse) will completely automate the process of setting up private key authentication from a client machine.

Private key authentication is the gold standard of SSH security. Provided the key was generated with good random material, and is kept secure on client systems, you have nothing to worry about from anyone armed with anything short of a quantum supercomputer.

---

### Post by TDrakeHI on 2010-11-28
Thank you all for your valuable information.  I will definitely be implementing a stand alone firewall over the next few weeks along with changing the SSH setup.

TDrakeHI

---

