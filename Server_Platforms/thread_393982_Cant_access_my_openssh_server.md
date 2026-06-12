---
title: "Cant access my openssh server"
date: 2007-03-26
forum: Server Platforms
---

### Post by computerjunkie on 2007-03-26
I installed the openssh server on my computer so I will be able to access my files from class through putty. I tested this out while I was in front of the computer by installing the client and connecting to myself and it worked fine. However, now that I'm in class when I try to connect it just times out. I think its because the router in the dorms blocks port 22. Is there a way to configure openssh to connect through another port, 80 for example, or could this problem be caused by something else other than a router blocking that port?


Also, I left the default settings as is. is that a huge security risk to my computer? All a person would have to do is portscan my IP, see the open port, connect, and guess my username and password and they would have access to my computer. Is there anyway to further authenticate connection requests to make sure it is me and not some random script kiddie or wanna-be hacker?

---

### Post by RichJacot on 2007-03-26
I assume you don't know what the dorm router is or is not blocking and your just wanting to try port 80?

Modify /etc/ssh/sshd_config.   Look for a line that has:
# What ports, IPs and protocols we listen for
Port 22
 
and change it to:

# What ports, IPs and protocols we listen for
Port 80

Then restart ssh or reboot.

I am also assuming you don't have a web server running on this box.

You may also want to try a high port if port 80 doesn't work.  I for instance use port 2222.  Just a thought.


As for your secondary question you can change your config to accept keys only and not password logins.

Hope this will help some.

---

### Post by conjur3r on 2007-03-26
The other thing you should look out for is if you need any port forwarding done on your router at home.  Your router may also be denying port 22 incoming so open that up as well.

So basically check both things:
1. Check if your dorm has port 22 out (try connecting to a public ssh server)
2. Check if your router has port 22 incoming port forwarded AND not denied

Default ssh settings on linux really sucks.  It's not quite as hardened as they should be but thank Ubuntu for disabling the root account!!  You really should deny root from logging in.  Also make sure that you have a strong password.  As RichJacot said, have a look at using public/private keys as a form of authentication.

---

### Post by computerjunkie on 2007-03-26
Well i dont have a router in my room, switches and routers arent allowed since we are authenticated on the college's network through our MAC addresses. (yes i know routers can clone, but then the admin would see a router he didnt name or extra broadcasts and it would be narrowed down to me which would suck majorly) Port 80 worked perfect, so the only logical conclusion is that port 22 is blocked on the schools routers (big surprise there *cough cough*)

Yea, I should prolly disable root logon, but in ubuntu it really doesn't matter since you can sudo with your normal password (which is very odd for linux compared to fedora, suse, etc). My normal password is pretty strong as I understand how easy it is to hack into most computers. 

Ok I have a couple more questions:

How do I set up public/private keys to authenticate a session?

Once I sucessfully logged into my computer from a windows computer in the lab i tried to copy a file from my home computer to the lab computer by using the cp command, but it didnt recognize the windows directory structure.

"cp /home/chris/example.txt C:\Documents and Settings\All Users\Desktop\example.txt"

The output said that "UsersDesktop" was not a directory. 

So how should I copy files from my home computer to another I might be sitting at if I need to access them?

---

### Post by gaten on 2007-03-27
>  How do I set up public/private keys to authenticate a session?This is a exept from a Howto I wrote: [http://www.ubuntuforums.org/showthread.php?t=383053](http://www.ubuntuforums.org/showthread.php?t=383053)


Generating the keys is a very simple process. First create a directory to store them in, then start **ssh-keygen**. Note, this needs to be done by the user you want to login through SSH as, **not root!**
```
mkdir -p ~/.ssh
chmod 700 ~./ssh
cd ~/.ssh
ssh-keygen -t rsa
```Something like the following should appear:
```

Generating public/private rsa key pair.
Enter file in which to save the key (/home/**USER**/.ssh/id_rsa):
Enter passphrase (empty for no passphrase):
Enter same passphrase again:
Your identification has been saved in /home/**USER**/.ssh/id_rsa.
Your public key has been saved in /home/**USER**/.ssh/id.pub.
The key fingerprint is:

```Obviously, **USER  **will be replaced with your actual user name. Now your private key is called **id_rsa**, and your public key is **id.pub.** 

The key idea here is you need **both** of these keys to log in. Your public key will be kept on your machine in the .ssh directory. Your private key will (ideally) be on your person, kept safe from the evil doers (I keep mine on my USB keychain). 

In order to conform to a default ssh server configuration, we're going to append your public key to another file.

```
cat ~/.ssh/id.pub >> authorized_keys
chmod 600 authorized_keys
```Now we're ready to configure sshd

[COLOR=DarkRed]**[SIZE=3]5. [/SIZE]**[/COLOR][U][B][SIZE=3][COLOR=DarkRed]Configuring SSH[/COLOR][/SIZE]

[/B][/U]Before we configure the ssh server, we have a couple of things to think about. First is where you're going to be connected to your computer from. Work? School? The local Starbucks? Now ask yourself, do they allow outbound connections on any port? If you're at school or work, the answer is mostly likely no. My school blocks all outbound ports <1024 (except for DNS, HTTP and HTTPS of course), but the higher number unassigned ports they tend to leave open. For instance, they block port 5900 (VNC), but they do not block port 47000 (unassigned). 

This is important information because we need to know what port to set up our ssh server on so that we CAN connect to it, no matter what. Here are some good guidelines (they don't apply in all situations of course)[LIST]
[*]High numbered ports (>1024) are blocked less than low ports (privileged ports)
[*]Some ports will almost always be open, like HTTP (80) and HTTPS (443). If all else fails, try running your SSH server on one of those.
[*]Last but not least, port 53 (DNS) will always be open.[/LIST]I run a web server on port 80, with SSL on port 443, so those options are out for me. So i chose a high numbered port (specifically 47000), and I have not had problems connecting from anywhere *yet*.

Now we're going to set SSH up to be a little more secure, and possibly to help us bypass any filters your school/work has set up.

First, let's make a backup of our SSH configuration (which we're going to change), in case anything goes wrong.

```
sudo cp /etc/ssh/sshd_config /etc/ssh/sshd_config.working
```Now, using your favorite text editor, open up **/etc/ssh/sshd_config**. A couple of changes are going to be made to this file. Find the line:
```
Port 22
```And change it to 
```
Port 47000
```Make sure there is no **# **in front of **Port. **You don't have to pick **47000**, but keep in mind what was said before.

Now we disable remote logins with the **root** account, find:

```
PermitRootLogin yes
``` and change **yes** to **no**. Even though the default Ubuntu install does not enable the root account, it is  a good idea to disable remote logins in case you decide to enable the root account at a later time (like I did).

Now we will disable password authentication **all together**. We do this for a couple of reasons:[LIST]
[*]You can't crack a password that doesn't exist.
[*]By doing this, we are **forcing** users to use public/private key authentication.[/LIST]Find ```
#PasswordAuthentication yes
``` and change it to```
PasswordAuthentication no
``` note that I removed the **#**.

Now we'll set up the server to use key pairs. Find
```
#AuthorizedKeysFile    %h/.ssh/authorized_keys
```And replace it with: ```
AuthorizedKeysFile  /home/**USER**/.ssh/authorized_keys
```Remember that file? We're telling the ssh server where to find our public key.
---

That should get you started. There are also some ideas about ports in there, I would choose 443 in your situation, if you can't find something larger than 1024 (try something really high like 55000). 

Also, allowing ONLY public/priv keys as authentication will pretty much eliminate all brute force attempts (unless they steal your key, then it's a whole 'nother ball game). 

>  So how should I copy files from my home computer to another I might be sitting at if I need to access them?You'll need to use **scp** or something. I like WinSCP, which has a nice little windows GUI kind of like most FTP guis. You set it up just like PuTTY. Get it here: [http://winscp.net/eng/index.php](http://winscp.net/eng/index.php)

The rest of my guide goes through setting up PuTTY, and also points you to a much better tutorial than mine for that purpose: [http://johnny.chadda.se/2006/10/24/access-your-linux-computer-graphically-and-securely-using-ssh-and-vnc/](http://johnny.chadda.se/2006/10/24/access-your-linux-computer-graphically-and-securely-using-ssh-and-vnc/)

Hope that helps.

---

### Post by conjur3r on 2007-03-27
> **computerjunkie said:**
> 
Once I sucessfully logged into my computer from a windows computer in the lab i tried to copy a file from my home computer to the lab computer by using the cp command, but it didnt recognize the windows directory structure.

If you need a nice gui to do this on the windows box, use FileZilla.  You will then be able to treat it as if it was a FTP server where you navigate to the folder you want and then move the files across the panels.

---

### Post by computerjunkie on 2007-03-29
alright thanks guys. that was really helpful.

---

### Post by huygens on 2007-03-29
You might want to look also at these articles :-)
[https://help.ubuntu.com/community/Security](https://help.ubuntu.com/community/Security) (there are a few entries about SSH)
[http://doc.gwos.org/index.php/SecureSSH](http://doc.gwos.org/index.php/SecureSSH) Securing SSH (featured article of the Month at GWOS!)

---

### Post by computerjunkie on 2007-03-31
well now I have another issue. I'm home on spring break trying to set up an ssh server on my dads computer so I can administrate it while away at school, but my router isn't letting me forward the ports. I have a linksys WRT54G router. 

                                          Port Range
Application 	Start 	End 	Protocol 	IP Address 	Enable

this is all I have to work with. under "IP address" it has "192.168.1" that cant be changed, only the last octet can be defined by the user so it seems that this router can only forward ports for known applications and only forward requests originating on this network (i.e computers connected directly, wired or wireless to this router). Unless that IP address slot is asking where to forward the requests. for the "application" field I tried entering "ssh", "openssh", "putty", and I tried leaving that field blank. I keep getting the same message "connection refused" on my other computer that I am trying to connect to this one using putty

:mad:  :mad:  :mad:  :mad:  :mad:  :mad:

geh my router hates me :( 


Please someone tell me what I'm doing wrong  

*router and computer flies through the window*

---

### Post by huygens on 2007-04-02
I went on the Linksys site and page 30 of the user guide I was able to figure out how to configure your router. You shall notice that the advertised port on the router will be similar as the one advertised on your computer. So if you have SSH running on port 22 (default), the router will have the port 22 open too.
So you have the various field to set-up:
Application 	Start 	End 	Protocol 	IP Address 	Enable

Application: give it a name like "Dad's SSH port"
Start: 22
End: 22
Protocol: TCP
IP Address: the IP address of your computer should be 192.168.1.nnn just set the nnn in the field.
And finally click "enable" and save the settings (button in the lower part of the screen).

That shall do it :-)

---

