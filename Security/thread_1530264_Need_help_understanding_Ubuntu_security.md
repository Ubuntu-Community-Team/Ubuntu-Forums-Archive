---
title: "Need help understanding Ubuntu security"
date: 2010-07-13
forum: Security
---

### Post by I_Want_To_Learn on 2010-07-13
Hello

First let me say I'm a long time Windows user so I have the "Windows Mindset". With Windows I have experience with the security "basics" (Malware scanners; software firewall,etc.) & classical HIPS with some sandboxing. I reformat Windows on a regular basics, so I'm not a "totally noob" to computers.

-->I have not installed Ubuntu 10 yet as I'm still trying to learn as much as I can before attempting.

For Ubuntu security, I'm currently reading these topics:

--> [http://ubuntuforums.org/showthread.php?t=510812](http://ubuntuforums.org/showthread.php?t=510812)
--> [http://www.psychocats.net/ubuntu/security](http://www.psychocats.net/ubuntu/security)
--> [http://www.itsecurity.com/features/ubuntu-secure-install-resource/](http://www.itsecurity.com/features/ubuntu-secure-install-resource/)

..but TBH, I feel very overwhelmed with the amount of information to learn. So I'm trying to get some help on what are the "must learn programs/information" & what are the optional stuff you need to know to achieve my goal. I'm also confused when I read users saying Ubuntu is secure by default & you don't need to do anything more but then you read topics explaining how to install & use HIDS, NIDS, Grsecurity, Apparmour, etc.

Goal: To achieve excellent overall security in Ubuntu 10 with the least amount of programs to learn & use.

--> Only plan to use Ubuntu for basic computer usage. No server, printing, P2P/Bittorrent, games, etc. Basically, just browsing the WWW.

--> I connect to the Internet via DSL. No router. No wireless.

What I've learned so far (please correct me if I'm wrong):

--> AV is not needed on Linux systems. It wouldn't hurt to use one if you transfer files to another Windows machine.

--> Iptables is the default firewall and in enabled from boot. You use "firewall config tools" like UFW, GUFW, or Firestarter to configure iptables.

So what do I need to do/learn to achieve my goal? Do I really need to learn how to use AppArmour, HIDS, NIDS or can those be optional? Are there any user-friendly alternatives to the above programs? I'm not asking for a handout, I just don't want to take months learning about stuff I wouldn't need. All I ask is to point me in the right direction.

On a similar note, I would like to know what are some symptoms of a compromised Ubuntu system? For example, in windows you'll see strange running processes, browser redirections, unknown program asking to open ports, etc. for clues that you are infected. Are there tools like Hijackthis! for Linux to try and spot infections?

Thank You

---

### Post by bodhi.zazen on 2010-07-13
Ubuntu is secure enough out of the box for your needs.

It takes up to 3-6 months to transition to a new OS, so you may dual boot for a while, nothing wrong with that option.

As time allows you can learn UFW, apparmor, but out of the box you are invulnerable to 99.9999 % of malware.

Just do not install servers, especially VNC or ssh, without learning to secure them first.

If you feel better with a firewall, open a terminal and enter

```
sudo ufw enable
```

By default there are no significant listening services, so there is nothing to firewall.

My advice is to relax and enjoy the high default security level. After you transition to Ubuntu you may wish to learn more about security. Keep in mind, security is a complex topic on any OS and Windows and the various security tools tend to hide the information rather then educate the end user. This builds dependency on various security tools such as antivirus and Norton.

Be free, break the addiction.

---

### Post by viralmeme on 2010-07-13
> **I_Want_To_Learn said:**
> Goal: To achieve excellent overall security in Ubuntu 10 with the least amount of programs to learn & use
Install Ubuntu 10 from the CD, create a username at the install stage, remove CD and reboot, that's it.

---

### Post by oldsoundguy on 2010-07-13
Been using some form of Linux since Mandrake 4.

Been using Ubuntu since 6.04.

Never installed any AV, Malware protection or any such foolishness.

Live behind a router firewall. NO server install.

Do not do stupid .. rely on repositories or approved sites such as Ubuntuzilla for any software.  Do not install the "hot new app" from some site I never heard of!

NO SECURITY ISSUES in all that time.

---

### Post by libssd on 2010-07-13
It's a delight to hear from someone who has done his homework. As others have already said, as long as you are not running a server, desktop Linux is secure by default (as opposed to Windows, which is insecure by default).

I would like to enable UFW, but when I do, I lose the ability to print to CUPS printers that are attached to my iMac. After a week of looking for clues, I'm still not clear how to resolve that one.

At this point, I would have to say that Linux security is an "interesting" pastime, but not something that I worry about much. My first year of running Ubuntu on a netbook included no thought whatsoever about security (nor have I had any problems).

---

### Post by I_Want_To_Learn on 2010-07-15
Well it's refreshing to hear how secure Ubuntu is "out-of-the-box". 

Just have a couple more questions (please be patient with me :D):

Keep reading to not use ssh &/or VNC (servers) unless you know how to secure them. On new Ubuntu install, these are not installed or enabled by default, correct?

In terms of network security, what are some things I should do/learn to prevent malicious users from connecting to my computer remotely then doing god knows what? Will a deny all incoming with UFW be sufficient enough? or are there additional steps I should take?

Thanks

---

### Post by bodhi.zazen on 2010-07-16
> **I_Want_To_Learn said:**
> Well it's refreshing to hear how secure Ubuntu is "out-of-the-box". 

Just have a couple more questions (please be patient with me :D):

Keep reading to not use ssh &/or VNC (servers) unless you know how to secure them. On new Ubuntu install, these are not installed or enabled by default, correct?

Correct

> In terms of network security, what are some things I should do/learn to prevent malicious users from connecting to my computer remotely then doing god knows what?

1. Use a router.

2. Before installing a server , learn to read it. SSH is a good place to start (if you are interested).

> Will a deny all incoming with UFW be sufficient enough? or are there additional steps I should take?

Thanks

Assuming you have a router, nothing further is required. First your router includes a firewall and second Ubuntu has no significant listening ports.

If you are on a public WAP , or do not use a router, I would enable a firewall. In that event:

```
sudo ufw enable
sudo ufw default deny
``` is sufficient.

If you want a graphical interface, take a look at gufw.

Under the hood, firewalls are a bit complex at first, see :

[http://bodhizazen.net/Tutorials/iptables/](http://bodhizazen.net/Tutorials/iptables/)

iptables is typically a little (or very) overwhelming at first, and that page may be overwhelming, start with the first few sections and continue if you want to learn more.

---

### Post by juancarlospaco on 2010-07-16
Do not use Firestarter, its development has stoped a long time ago

---

### Post by oomar on 2010-07-16
honestly, dont do anythign stupid and youll be fine. I don't mess around with ip tables as i dont need the complex configuration it can provide. all i need is a few open ports for my servers (ssh, web, squid proxy, webmin) then i harden them and viola. pretty darn secure system. 

just enable UFW and learn it from CLI (honestly after reading the man page twice you should be able to use it more efficiently than GUFW) 

> In terms of network security, what are some things I should do/learn to prevent malicious users from connecting to my computer remotely then doing god knows what?

if you only have the ports open that you NEED and secure the applications using them appropriately (ie if you use ssh, set to non-default port, no login as root, key-only authentication) people shouldnt be able to connect to your computer remotely at all.

---

### Post by iponeverything on 2010-07-16
imo in using a non-default port for ssh server buys nothing. 

It takes almost no effort to scan all 65535 ports on a machine to locate a listening ssh server. 

ssh key only very secure.  

@bodhi.zazen is totally sound in his advice to just jump in and enjoy, there are very few nasties in this lake. 

I have been in the business of linux admin for many years, default installs used to have everything under the sun running by default -- 

Keep in mind for below that a lot has changed -- it has been years since sendmail, bind, portmapper, imap and other services have caused problems.

Back in the day, my first thing after doing an install was to shutdown or filter the ports for all the services. The way that Ubuntu does in very good, start secure. 

It is quite easy to undermine you own security -- what I see most often these days is problems somewhere in LAMP application stack.  Setting up a LAMP server is easy, understanding how to secure and monitor it after you install a complex php application that it too large to audit is not.

---

### Post by linux18 on 2010-07-17
When I had my desktop I kept it running 24/7 for months at a time with firefox always opened to six different sites.

My security policy:
-I never used any AV software
-never used a firewall ( except the very basic one built into my routers firmware )
-I always saw firefox's messages saying "this site may be malicious" as a challenge
 
The one thing I did do:
-only install software from from the repositories and only run shell scripts when I work out what they do


Now that desktop is serving linux awesomeness to someone who couldn't afford a computer and still runs 24/7. BOTTOM LINE: no viruses at all ever.

the linux malware wikipedia page:

[http://en.wikipedia.org/wiki/Linux_malware](http://en.wikipedia.org/wiki/Linux_malware)

although it is important to note that a normal desktop user that ( like me ) only gets software from the repositories can only possibly catch a virus through directed attack ( *they* are targeting only your computer ) or in the wild ( too many windows comparisons to name ) and wild linux viruses are unheard of because they don't propagate between computers very well.


If your switching from windows to lnux unlearn these things:

-antivirus       
-defragmentation
 -AOL toolbars         
-registry anything
-finding new versions of installed software                    
-C: D: E: etc.


And quickly learn these things:

-terminals                     
-package management ( synaptic )                    
-directory structure 
-compiling from source is ****ing hard the first few times          
-sudo !! ( rerun the last command but with sudo, because you will forget to sudo big commands occasionally   )
  
The best way to learn is to try, so download an iso, burn it to disk, and try the live cd ( as long as you dont mess with the windows partition ( and it will be obvious if you are ) or delete anything on the windows drive, then you should be completely fine trying out the live cd. ) the live cd is where you can learn linux while being one reboot away from the windows your used to.

Have fun with linux

---

### Post by I_Want_To_Learn on 2010-07-28
Hello

I now have a quick ? about user accounts/sudo.

What are the security benefits gained from using a user account with no sudo access for daily use? Is it worthwhile for the extra hassle it will add? For example, if I would want to edit my UFW rules I would have to log in to my admin. account since that action requires sudo rights,correct?

TY

P.S. Thanks for the replies. I'm learning.:D

---

### Post by ahbart on 2010-07-28
> **I_Want_To_Learn said:**
> What are the security benefits gained from using a user account with no sudo access for daily use? Is it worthwhile for the extra hassle it will add?
Unnecessary difficult. Just use a good password.

---

### Post by bodhi.zazen on 2010-07-28
> **I_Want_To_Learn said:**
> Hello

I now have a quick ? about user accounts/sudo.

What are the security benefits gained from using a user account with no sudo access for daily use? Is it worthwhile for the extra hassle it will add? For example, if I would want to edit my UFW rules I would have to log in to my admin. account since that action requires sudo rights,correct?

TY

P.S. Thanks for the replies. I'm learning.:D

The benefits of a day to day user outside of the admin group are minimal.

If you are worried about it, set your sudo security a bit tighter :

[https://wiki.ubuntu.com/SecurityTeam/FAQ#Sudo](https://wiki.ubuntu.com/SecurityTeam/FAQ#Sudo)

---

### Post by I_Want_To_Learn on 2010-08-15
Hello again!

Have 2 "noobish" questions about malicious files.

1) If I decided to download files (videos, music,etc.) from untrusted sources (Ex. P2P) on Computer A, but just transfer them via external media to Computer B, is there still a risk of getting Computer A infected? In other words, to infect a computer with a malicious file the file has to be opened or executed, correct?

2) I have a USB stick I used on what I would call "untrusted computers". How can I securely wipe the USB stick, without having anything malicious (if they exist) automatically transfered over to my computer when plugged in? What are my options? 

As always, Thank You.

---

### Post by bodhi.zazen on 2010-08-15
> **I_Want_To_Learn said:**
> Hello again!

Have 2 "noobish" questions about malicious files.

1) If I decided to download files (videos, music,etc.) from untrusted sources (Ex. P2P) on Computer A, but just transfer them via external media to Computer B, is there still a risk of getting Computer A infected? In other words, to infect a computer with a malicious file the file has to be opened or executed, correct?

2) I have a USB stick I used on what I would call "untrusted computers". How can I securely wipe the USB stick, without having anything malicious (if they exist) automatically transfered over to my computer when plugged in? What are my options? 

As always, Thank You.

It depends on what OS the two computers are running, the type of malicious file, and what OS the exploit is written for.

In general, if you download a file which contains a windows virus it will not affect Linux. You can transfer the file, and thus the virus, to a windows computer.

In general, you have to open a file or run a program to unleash the virus (depends on the virus).

what you should probably do with a shared drive:

1. On your Linux box, install antivirus and scan the flash drive for viruses.

2. On your windows box, disable all auto run features, windows should do nothing when the drive is inserted. Scan the flash drive with windows antivirus. If it is clean, then go ahead and open the drive, transfer files, etc.

You should be doing all this already windows side. Antivirus Linux side is less useful, but if you share with Windows then there may be some benefits.

---

### Post by rookcifer on 2010-08-15
> **linux18 said:**
> When I had my desktop I kept it running 24/7 for months at a time with firefox always opened to six different sites.

My security policy:
-I never used any AV software
-never used a firewall ( except the very basic one built into my routers firmware )
-I always saw firefox's messages saying "this site may be malicious" as a challenge
 
The one thing I did do:
-only install software from from the repositories and only run shell scripts when I work out what they do


Now that desktop is serving linux awesomeness to someone who couldn't afford a computer and still runs 24/7. BOTTOM LINE: no viruses at all ever.

the linux malware wikipedia page:

[http://en.wikipedia.org/wiki/Linux_malware](http://en.wikipedia.org/wiki/Linux_malware)

although it is important to note that a normal desktop user that ( like me ) only gets software from the repositories can only possibly catch a virus through directed attack ( *they* are targeting only your computer ) or in the wild ( too many windows comparisons to name ) and wild linux viruses are unheard of because they don't propagate between computers very well.


If your switching from windows to lnux unlearn these things:

-antivirus       
-defragmentation
 -AOL toolbars         
-registry anything
-finding new versions of installed software                    
-C: D: E: etc.


And quickly learn these things:

-terminals                     
-package management ( synaptic )                    
-directory structure 
-compiling from source is ****ing hard the first few times          
-sudo !! ( rerun the last command but with sudo, because you will forget to sudo big commands occasionally   )
  
The best way to learn is to try, so download an iso, burn it to disk, and try the live cd ( as long as you dont mess with the windows partition ( and it will be obvious if you are ) or delete anything on the windows drive, then you should be completely fine trying out the live cd. ) the live cd is where you can learn linux while being one reboot away from the windows your used to.

Have fun with linux

Very well said.

---

### Post by dave-buntu on 2010-08-16
I also recommend that you install all the security updates for 
your system.

---

### Post by Master Cabbage on 2010-08-29
> **dave-buntu said:**
> I also recommend that you install all the security updates for 
your system.

I'm assuming if your update manager says you have all of the required updates then you are good security wise, right?

---

