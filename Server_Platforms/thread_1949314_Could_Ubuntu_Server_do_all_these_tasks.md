---
title: "Could Ubuntu Server do all these tasks?"
date: 2012-03-29
forum: Server Platforms
---

### Post by Unewbeginner on 2012-03-29
hello everyone, I'm not a server expert and I'd like to if Ubuntu Server could handle the situation below in our company:

- about 50 workstations with different OS (Ubuntu, Windows, Mac)
- All these workstations could communicate with each other (email, instant messenger, etc)
- All these workstations could access a File Server
- Different file permissions for different level of employees
- The IT manager could deploy all the services and permissions above, but the general manager has a higher level of IT authority than him.

If everything is possible with Ubuntu Server, any good suggestions on the specific tasks? Like which software to do the file permissions assignment, etc?

Thanks in advance!

---

### Post by drdos2006 on 2012-03-30
Of course Ubuntu can do all you ask of it.
If you are going to be the administrator of the equipment then you are going to have to do some heavy reading to set up your first server.
Zentyal will get your machine running in an office environment while you learn the more detailed operations of a server. [http://www.zentyal.org/](http://www.zentyal.org/)
Uses a GUI at the server, was based on Ubuntu 10. Long Term Support last time I looked.

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

### Post by Unewbeginner on 2012-03-30
Thanks, How could I manage all the users with different OS? Mainly the file access permissions assigned to different level of employees. Someone told me it's impossible for a multiple OS network. Is this true?

---

### Post by rk0r on 2012-03-30
Wht i have noticed that with multiple OS and file servers is the permissions level you highlighted in your previous post. 

On my setup the UNIX laptop can see hidden files on the shared drive as standard. 

To make life easy its best practice is to keep to one variant of OS and then setup the network from there. 

can of worms comes to mind.

---

### Post by koenn on 2012-03-30
> **drdos2006 said:**
> Of course Ubuntu can do all you ask of it.
I wouldn't bet my job on that.

---

### Post by Lars Noodén on 2012-03-30
For the file sharing you'll want to look at Samba:
[https://help.ubuntu.com/community/Samba](https://help.ubuntu.com/community/Samba)

For mail, calendaring and other groupware, you can take a look at Citadel or Kolab:
[http://citadel.org/](http://citadel.org/)
[http://kolab.org/](http://kolab.org/)

---

### Post by richardjh on 2012-03-30
We have an Ubuntu box working as a file server using Samba.

I have found the Windows clients saves everything with 755, the linux clients as 644. This is a nuisance as if a Linux user creates a new file, a user on a windows client machine cannot edit it unless the permissions are changed.  I haven't found a solution but perhaps one exists. UPDATE - Forget it. I was connecting my Linux client over ssh. :) D'oh

Another issue that may arise in the future is that file servers often end up working as print servers too. There are well supported printers, there are also completely-not-supported printers. 
Have a think about who buys the printers in your company and how likely it is they will consider Linux driver issues.

If you are responsible for the security of the files, you will have to do your own testing to make sure you are happy you can lock things down correctly.

With regards to software, Lars has made some pretty good suggestions. 
I additionally use it to run an IRC server using[ dancer-ircd]("https://help.ubuntu.com/community/Dancer-IRCD"), and as a backup server using [BackupPC]("https://help.ubuntu.com/community/BackupPC").

I am all for pushing Ubuntu wherever possible but ultimately you have to decide if it is the best solution for your situation. Sounds to me like you are trying to put this case forward as the perfect solution and looking for something to back it up. It is encouraging to hear some positive replies here but I can not honestly say that you will have no issues, even if you do install webmin. :)

---

### Post by darkod on 2012-03-30
> **richardjh said:**
> We have an Ubuntu box working as a file server using Samba.
I have found the Windows clients saves everything with 777, the linux clients as 644. This is a nuisance as if a Linux user creates a new file, a user on a windows client machine cannot edit it unless the permissions are changed.  I haven't found a solution but perhaps one exists. 


You sound like you know much more than me on this subject, but one thought occurred to me.

If you want the written files to be editable by anyone, not just the same user, how about forcing a user/group on the samba share. That way, regardless if using the share from windows or linux client, you are forced to create the file as the same user, and in future you have full access too.

---

### Post by Habitual on 2012-03-30
> **Unewbeginner said:**
> ...- The IT manager could deploy all the services and permissions above...

every IT "Mangler" I have ever known could not deploy a rubber duck in a bathtub. ;)

---

### Post by Dangertux on 2012-03-30
> **Unewbeginner said:**
> hello everyone, I'm not a server expert and I'd like to if Ubuntu Server could handle the situation below in our company:

- about 50 workstations with different OS (Ubuntu, Windows, Mac)
- All these workstations could communicate with each other (email, instant messenger, etc)
- All these workstations could access a File Server
- Different file permissions for different level of employees
- The IT manager could deploy all the services and permissions above, but the general manager has a higher level of IT authority than him.

If everything is possible with Ubuntu Server, any good suggestions on the specific tasks? Like which software to do the file permissions assignment, etc?

Thanks in advance!

What instant messaging service you trying to use? Office communicator? If so...Cough up for a Windows license, you might be able to get SIP working on nix, but...The man hours involved would be more costly than the Windows license.

---

### Post by SeijiSensei on 2012-03-30
How to implement the two-tiered system of authority you describe isn't obvious to me. but here are some thoughts on the matter.

Unix systems generally make a distinction between the "root" user, which owns most of the files on the system and has global read/write permissions, and all other users who typically have read/write permissions to their own home directories and /tmp.  Ordinary users may have additional permissions in other directories as determined by their membership in user groups. 

The root user has other exclusive permissions as well such as user account management and running "daemon" programs that listen on TCP/UDP ports between 0 and 1023.  Ordinary users cannot, for instance, run an SMTP daemon that accepts mail on the standard port 25; only root can run a program that binds to that port.

Thus, if the "IT manager" has root permissions, he or she can do essentially anything on the server.  There is no higher level of authorization which can be assigned to the "general manager."  What specific functions does the GM wish to control exclusively?  

You could separate the user account management function from management of the services like file sharing and mail.  You would do this by running a network authentication service like LDAP, NIS, or RADIUS on one server and grant root access on that box to the less-privileged manager.  That person could then create, delete, and manage user accounts.  The other server(s) would be configured to authenticate against the account server, and root access to those machines granted to one or more other administrators.  You might run a separate mail server, for instance, and grant root access to that machine to a person designated as the organization's mail administrator.

As for file sharing, you can run both NFS and Samba on the same server and use NFS to export shares to *nix machines and Samba to export shares to Windows machines.  I don't know whether Macs, being Unix-based, work better with NFS or CIFS (Samba) filesystems, but others here would know.  My office server exports users' home directories using both protocols.  I mount my home directory on my Linux machines using NFS and map that directory to a drive letter in Windows with CIFS.

---

### Post by Unewbeginner on 2012-03-31
> **Lars Noodén said:**
> 
For mail, calendaring and other groupware, you can take a look at Citadel or Kolab:
[http://citadel.org/](http://citadel.org/)
[http://kolab.org/](http://kolab.org/)

Thanks! Both look pretty good. I will check them out!

> **SeijiSensei said:**
>  Ordinary users may have additional permissions in other directories as determined by their membership in user groups. 

Is it possible that these user groups are under different OS? For example: there are 2 user groups: team A, team B. Team A uses Ubuntu, team B uses Windows. They share a file server and write and read files to the server in their daily work. There are many different kinds of folder on the server, with different file access permissions. 


> **SeijiSensei said:**
>  Thus, if the "IT manager" has root permissions, he or she can do essentially anything on the server.  There is no higher level of authorization which can be assigned to the "general manager."  What specific functions does the GM wish to control exclusively?  

Basically we are trying to avoid IT manager to get the highest authority without any limits. If only the IT manager get the root password, what if he quits someday and unwilling to provide the password?

> **SeijiSensei said:**
> You could separate the user account management function from management of the services like file sharing and mail.  You would do this by running a network authentication service like LDAP, NIS, or RADIUS on one server and grant root access on that box to the less-privileged manager.  That person could then create, delete, and manage user accounts.  The other server(s) would be configured to authenticate against the account server, and root access to those machines granted to one or more other administrators.  You might run a separate mail server, for instance, and grant root access to that machine to a person designated as the organization's mail administrator.

In the solution you suggested, would it be a good idea to let the most reliable guy (the boss?) control the user accounts management, and just ask some ordinary system admin to manager a certain kind of service (mail, wiki, etc)?


> **SeijiSensei said:**
> As for file sharing, you can run both NFS and Samba on the same server and use NFS to export shares to *nix machines and Samba to export shares to Windows machines.  

Is it possible to just use Samba for all OS?

Thanks again for your detailed answer!

---

### Post by SeijiSensei on 2012-03-31
> **Unewbeginner said:**
> Is it possible that these user groups are under different OS? For example: there are 2 user groups: team A, team B. Team A uses Ubuntu, team B uses Windows. They share a file server and write and read files to the server in their daily work. There are many different kinds of folder on the server, with different file access permissions.

Yes, you can do this with a combination of [Unix]("https://help.ubuntu.com/community/FilePermissions") permissions and [Samba]("http://www.samba.org/samba/docs/man/Samba-HOWTO-Collection/rights.html") permissions. 

> Basically we are trying to avoid IT manager to get the highest authority without any limits. If only the IT manager get the root password, what if he quits someday and unwilling to provide the password?

You can always reset the root password from the console by booting into single-user mode.  The "recovery mode" option presented at boot by Ubuntu enables this.

> In the solution you suggested, would it be a good idea to let the most reliable guy (the boss?) control the user accounts management, and just ask some ordinary system admin to manager a certain kind of service (mail, wiki, etc)?

Personally I think you need to have the most trusted person in charge of the mail server.  That person will be able to read everyone's mail.  I see user account management as a pretty low-level task.  Someone joins the company, and the account manager adds the person to the authentication server.  Seems like a pretty rote task to me.

> Is it possible to just use Samba for all OS?

For Windows and Linux the answer is yes.  I suspect that's also true for Macs, but I don't have any experience with that platform.

---

### Post by kevinthecomputerguy on 2012-03-31
Samba can handle all of your file sharing needs, cross all three platforms, and get the file permissions right every time. It is true that you will be able to see hidden files and or hidden shares from linux, but hidden files and hidden shares shouldn't be used as security features anyway.

As the poster above mentioned, mapping drives and home dirs can be a pain cross-platform, but if you can teach your users (or make them a shortcut) then it gets much easier.

On windows you can connect by typing \\ipaddress  in a windows explorer window.

On Mac and Linux, you type smb://ipaddress in your file chooser or "go to" window.

I give a walk through on page 3, about halfway down, but best to start at page 1.

[http://woodel.com/page3](http://woodel.com/page3)

-Kevin

---

### Post by HermanAB on 2012-04-01
> "Windows clients saves everything with 777, the linux clients as 644"
This user should read the Samba book and configure it properly...

---

### Post by richardjh on 2012-04-02
> **HermanAB said:**
> This user should read the Samba book and configure it properly...


Thanks HermanAB. I am glad you took the time to post this information.

I really could not work out a way to resolve the issue but now, thanks to your help, I can see the solution. 
I will get on and read the Samba book and configure it properly right away. :)

( Sorry for the dig, I am just in a silly mood this morning. Combination of sunshine and tea I suspect. )

I did have a look into this after I posted and it turns out I was  mounting the share from my Linux client over ssh and not samba. D'oh!

---

