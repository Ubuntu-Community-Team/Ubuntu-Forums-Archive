---
title: "Need Help With Server Set-up"
date: 2012-02-02
forum: Server Platforms
---

### Post by chughes27 on 2012-02-02
So, for a course I'm taking I am required to set up a new server for my school. The current server does not have the space or the power to support the amount of computers we have constantly running. Every student is allocated a certain amount of disk space in a virtual drive that they can access from any computer on the school network, and at the moment each student gets only 500 Mb, which for most is a pretty big issue. 

We already have a few towers set up with Ubuntu 11.10 Desktop that we are going to use for the server, and my course instructor does not seem to think we need to have Ubuntu Server, says we can do this with the desktop edition. 

I am not at all experienced with setting up a server, and I need all the help I can get. 

Thanks!


NOTE -- I will be getting some specs of the towers later tomorrow, so that I can provide an accurate description of what I have to work with.

---

### Post by Mia1990 on 2012-02-03
There is very little difference between Ubuntu desktop and Ubuntu server the server doesn't install a gui so it's headless it contains server specific packages in place of desktop components and Ubuntu server installs a server optimised kernel.

[Here]("https://help.ubuntu.com/community/ServerFaq") is a link you may be interested in ubuntu desktop vs ubuntu server.

* *

---

### Post by bubylou on 2012-02-03
Ubuntu server is much more light weight that the desktop edition. If you need to utilize as much of your hardware as possible then use the server. There is no reason to have a GUI taking up resources on a server.

---

### Post by chughes27 on 2012-02-03
Its not going to be a very complex set-up, it turns out we are just going to hosting a small FTP server on the one tower we have set up with Ubuntu 11.10. We are using the desktop Ubuntu because we want to have more ease of use and be able to see everything we're doing.

---

### Post by bubylou on 2012-02-03
i would still recommend Ubuntu Server over Desktop personally. I rather enjoyed the learning experience and it really isn't that steep of a learning curve. But if desktop fits your needs then do whats best for you.

---

### Post by TheFu on 2012-02-03
Note really the question that you asked, but very few people should use FTP anymore, ever.  I'd be afraid to use any insecure protocol on a college LAN.
There other, better options for most use-cases. [http://blog.jdpfu.com/2011/07/10/why-you-need-to-stop-using-ftp](http://blog.jdpfu.com/2011/07/10/why-you-need-to-stop-using-ftp)

Of course, there are a few specific cases where plan FTP does make sense, but many of the most capable and popular FTP servers have had backdoors added to their code for months (perhaps years?) before anyone noticed.

---

### Post by chughes27 on 2012-02-04
Well is there any way to make an FTP more secure? We wouldn't really want someone on the outside of our school to be able to access our files and such.

---

### Post by volkswagner on 2012-02-04
> **chughes27 said:**
> Well is there any way to make an FTP more secure? We wouldn't really want someone on the outside of our school to be able to access our files and such.

I think the answer was mentioned.. Don't use ftp but do use sftp.

You can still use FTP clients to access the machine... Filezilla supports SFTP and also many others do also.  This is just a matter of setting up ssh.  Once you have ssh setup, you can use sftp to access the box.

Are you going to access this on the LAN only? I'd imagine you would need permission and access to the school network to open ports for access outside the LAN.

---

### Post by chughes27 on 2012-02-04
> **volkswagner said:**
> Are you going to access this on the LAN only? I'd imagine you would need permission and access to the school network to open ports for access outside the LAN.

That makes a lot of sense actually, all of the computers we use the most are connected to our network with cables. So yes, I'd think that you'd need to connected to the school's network to access it. 

And its not like we're going to be just telling everyone the port numbers and all that. The files we need to share will just be in the form of links on our school's website.

---

### Post by drdos2006 on 2012-02-04
Here is a HOWTO which I found comprehensive and invaluable for me to start learning about server requirements. 
Uses Webmin to allow your browser to connect and modify your server settings.
You could also install the Desktop plus install and run the server as a virtual machine using Virtualbox and that is how I run my testing websever.

> 
Are you using the most current version of this how-to?
Version numbers are located @ top right of this page. Latest versions are available at my homepage [http://woodel.com](http://woodel.com)
Under the Solutions tab
"Setting up a Linux Server, Start to Finish, using Webmin". By Kevin Elwood



And on your server..........

```

Logon to your server and download from your server with :
sudo wget http://prdownloads.sourceforge.net/webadmin/webmin_1.570_all.deb

Install with :
sudo dpkg -i webmin_1.570_all.deb

Add extra libraries with :
sudo apt-get -f install

```
Uses a browser pointed to [https://server_IP:10000](https://server_IP:10000) to edit files, create shares, startup daemons etc..

regards

---

### Post by chughes27 on 2012-02-04
@drdos2006: Thanks! Just wondering though, is Webmin compatible with MySQL? And is it pretty easy to use?

---

### Post by Vegan on 2012-02-05
webmin supports the full LAMP stack including MySQL and a bunch more

---

### Post by chughes27 on 2012-02-05
great! I tried it out a little earlier, and I'm afraid I don't really understand most of it. Can someone post a walk through or a guide to using webmin? 

Thanks!

---

### Post by kevinthecomputerguy on 2012-02-05
I think Drdos already did that for you.

*my guide doesn't cover mysql, but webmin does support it and or the file manager makes that easy enough to edit.

---

### Post by drdos2006 on 2012-02-05
You need to go through Kevins guide to find out what you can do with the server. Once you know what you want the server to do, then you use Webmin to administer the server. Kevins guide is very comprehensive for new server administrators.

Webmin can share folders, change permissions for folders, edit configuration files, set up MySql users and passwords, set up PostgreSQL, in fact Webmin is so useful that I run it on my desktop ( 10.4 LTS ) to accomplish taks that would normally require me to use the terminal.

As with all things, it takes time and practice to learn new material.

Show your teacher how easy it is to administer a server via the browser with Webmin, your class mates might learn something new as well. Print out some of Kevins guide and have it beside you when you get to some tricky stuff. Keven wrote the guide using Debian, Ubuntu is based on Debian. When you read Debian, think Ubuntu.

Lots of praise to Kevin for the time and effort it took him to develop the manual. He also has some very nice videos on RAID setup as well. Read the guide first.

regards

---

### Post by chughes27 on 2012-02-07
I found that wasn't exactly helpful to what I'm doing, for one I'm not doing this on the server edition of Ubuntu I'm using the desktop version. And I'm not trying to set up a very complex server, I'm just trying to set up a small FTP that each user on the school's network can access. 

What I need is some FTP software that can connect to the accounts on our school's network and allow certain users to access their own personal folders as soon as they log in, and not be able to access anyone else's. Pretty much what I'm saying is I want to store everyone's folders on the server, and allow them to remotely access it from their own computers. This is absolutely essential to the project.

Thanks for all the help so far, I'm looking forward to hearing more!

---

### Post by kevinthecomputerguy on 2012-02-07
A great way to paraphrase this would be&#8230; would you tell that to your locksmith :- )

I don&#8217;t know if simple and absolutely essential really ever merge.

Here is what would happen if you went with a simple ftp solution. ftp sends everything in plain text, so a hacker on your network would see something like this...

"User 192.168.2.2 would like to ftp to server 192.168.2.1 and his username is _john.smith_ "
    "Ok, john.smith what is your "_password?_ "
John.smith@192.168.2.2 password was entered is : _"turkeySandwhich1 "_
    Ok, that&#8217;s the right username and password john.smtih, enjoy your ftp&#8217;ing

So a hacker takes that info above and does this. Since EVERYONE uses the same password for everything in their life, he&#8230;

Tries to get into their computers c:\ drive by typing \\192.168.2.2\c$  with username jsmith and that same password. 

If that doesn&#8217;t work, he waits until 6pm, when everyone has gone home, and remote desktops that user by typing mstsc.exe /v 192.168.2.2 with username jsmith and that same password.

Not satisfied that he has totally owned your computer, and copied \ then deleted all the files, he decides to try your Bank of America login at bofa.com, it doesn&#8217;t work, so he tries john.smith  at gmail.com and at [https://mail.yourcompany.com](https://mail.yourcompany.com) and voila, both work.

So he goes back to bofa.com, hits the password reset button, your password is sent to the email addresses above, and you&#8217;re broke.

So, would you tell your locksmith you wanted something simple :- )

Here is an sftp how to, it&#8217;s fairly straight forward, but you&#8217;re going to do heavy reading if your users depend on you for their security needs. [http://woodel.com/domore/sftp/woodel_sftp.pdf](http://woodel.com/domore/sftp/woodel_sftp.pdf)

---

### Post by chughes27 on 2012-02-07
Well if ftp is that insecure, what other option do I have for the setup I need? If my explanation is not clear enough, please let me know and I'll try and clarify it some more.

Thanks

---

### Post by BenWuan on 2012-02-07
I think @KevinTheComputerGuide already posted you an (s)ftp link above?
"S" meaning secure.

---

### Post by Amanitas on 2012-02-07
Check again the meaning of SFTP. SFTP stands for SSH File Transfer Protocol. This is not FTP though SSH but instead the protocol SSH uses to transfer files.

FTPS is what I believe you are trying to say which is FTP through SSL. 

Don't want you to go looking for the wrong things now

[edit] they are both secure though

---

### Post by kevinthecomputerguy on 2012-02-07
Rest assured both my link and my recommendation are for sftp (ssh) and not ftps

---

### Post by chughes27 on 2012-02-08
Alright well I'm following your sftp guide right now, but right off the bat I have a problem. When I go to edit the /etc/ssh/sshd_config file, its completely empty. I have nothing to edit.

---

### Post by Amanitas on 2012-02-08
[http://ubuntuforums.org/showpost.php?p=6492152](http://ubuntuforums.org/showpost.php?p=6492152) may help

[btw, was your original question to get a webserver?]

---

### Post by kevinthecomputerguy on 2012-02-08
Thats odd, try

sudo apt-get update
sudo apt-get install ssh

If that doesnt work try.

sudo apt-get remove ssh
#assuming u have local access and arent connected via ssh, dont do this if ssh is your only connection
sudo apt-get upgrade
sudo apt-get install ssh

---

### Post by chughes27 on 2012-02-08
I didn't do any of that, turned on my computer this morning and decided to just see if it would work, and all of a sudden the file is full...every time I install Ubuntu I seem to always have really weird issues lol...

But it works now at least

---

### Post by chughes27 on 2012-02-08
Well now the /etc/network/interfaces file has nothing in it that your tutorial says to edit, and when I add the contents manually my computer reboots without any option to connect to my schools ethernet! I restored the file to the way it was, so now its empty again and I have no way of moving on in this tutorial.

Please help!!

---

### Post by drdos2006 on 2012-02-08
> 
We already have a few towers set up with Ubuntu 11.10 Desktop that we are going to use for the server, and my course instructor does not seem to think we need to have Ubuntu Server, says we can do this with the desktop edition.

From your first post, I see you are running the Desktop version. The Desktop version uses Network Manager to administrate and control the Network interfaces. 
If you are runing the Desktop, use Network Manager to set fixed IP address. 
If you run the server edition, edit /etc/network/interfaces file.

regards

---

### Post by chughes27 on 2012-02-08
I'll try that when I'm back in my class tomorrow. Thanks.

---

### Post by chughes27 on 2012-02-08
@drdos2006: I tried this out on my ubuntu computer at home, I have no application called "Network Manager" (I did a search) and any application I do have that has anything to do with my network do not give me an option to set a static ip address.

Any ideas?

---

### Post by drdos2006 on 2012-02-08
My version of Ubuntu is 10.4. My Network Manager is under System -> Preferences -> Network Tools. I have no idea of Ubuntu 11.10 or 12.04.

regards

---

### Post by chughes27 on 2012-02-09
Alright mine comes with network tools as well, how do you create a static IP from there though?

---

### Post by kevinthecomputerguy on 2012-02-09
I miss read your original post, i didnt realize you were using the desktop version, sorry, i cant be of much help from here on. Best of luck, there are alot of people here with good advice that can help you with that version and your project.
-Kev

---

### Post by chughes27 on 2012-02-09
So your tutorial won't work at all with the desktop version?

---

### Post by kevinthecomputerguy on 2012-02-09
I know 0% about the desktop version, sorry i cannot be of further help.

---

### Post by bubylou on 2012-02-09
if your looking for a secure form of file transfer then i know Ubuntu server has the vsftpd package which you can use ssl to make it secure. But if if you already have openssh installed then maybe sftp would be a better choice. I use sftp personally but you should read up on the differences between the 2. Try[ this]("http://www.codeguru.com/csharp/.net/net_general/internet/article.php/c14329") to get you started.

---

### Post by chughes27 on 2012-02-09
I've been doing a lot of research lately, I'm going to have to install Ubuntu server. I have no idea why my instructor didn't want me to set up a server in an OS that's actually made for servers. 

Any advice with using Ubuntu server? If I install it with a user interface is that just like installing Ubuntu desktop or will it still have all the capabilities of Server? 

Thanks again everyone

---

### Post by drdos2006 on 2012-02-09
All the advice you have been given here recommends using a server rather than a desktop. Congratulations, you have made the correct choice.
Now go back to my first post and continue from there.
If your machine has enough harddrive space and RAM then you could install a Virtual server on your equipment with Virtualbox rather than re-installing server software on your desktop.

regards

---

### Post by chughes27 on 2012-02-10
I don't think removing Ubuntu desktop will a big loss to me, as all I have done with it so far is mess with it. Besides, I would like to use the most amount of hard disk space as I can. Using a virtual server would just take up more much needed space. A big component of the project is minimizing the amount of space I use for the system and software and maximizing the amount of space everyone on the network is given.

---

### Post by bubylou on 2012-02-10
Ubuntu server doesnt come with a gui by default but you can install one, but once again it is not recommonded. Here is a [quick guide]("https://help.ubuntu.com/community/ServerGUI") for you that also lists why not to use a gui. I strongly recommend learning how to navigate the command line.

---

### Post by chughes27 on 2012-02-10
Thanks for the advice. I'll be setting it up today and I'll be checking back later and let everyone know how it's going.

---

### Post by chughes27 on 2012-02-10
So, got it all set up. Strapped in an extra hard drive and I think I'm now ready to go. 

One question, is a "home" file server the same as a school file server? And if I do set up a home-type server, will it require users on different computers to install software to be able to access their files? Or will they just show up as a virtual drive as soon as they log in?

---

### Post by drdos2006 on 2012-02-10
Once you install your server you need to install a Secure FTP program on the server.

[http://www.cyberciti.biz/faq/ubuntu-vsftpd-ftp-service-server/](http://www.cyberciti.biz/faq/ubuntu-vsftpd-ftp-service-server/)

Using Webmin from a Desktop to access the server users, groups and quotas can be set up for each user.

Under Webmin, "Disk and FileSytems" you can configure disk space for your users through "Quota" and also reserve space for your "User" who you have added as a user.

Your users would then have to install software on their desktops, such as Filezilla, to access the shares you have nominated for each user.

Kevins manual describes these procedures.

regards

[http://www.google.com/search?client=ubuntu&channel=fs&q=secure+ftp+ubuntu&ie=utf-8&oe=utf-8](http://www.google.com/search?client=ubuntu&channel=fs&q=secure+ftp+ubuntu&ie=utf-8&oe=utf-8)

---

### Post by bubylou on 2012-02-10
Is ftp really what your looking for. It sounds to me like [samba]("https://help.ubuntu.com/11.10/serverguide/C/windows-networking.html") might better for you but im not really well acquainted with your current network. It will definitely have more features than ftp.

---

### Post by chughes27 on 2012-02-14
No, I will not be using FTP. I'm setting up a Samba file server.

---

