---
title: "SSH and FTP problem!"
date: 2017-06-22
forum: Security
---

### Post by pink-hat on 2017-06-22
hello

I am the new one.

actually I have problem.

I work with Kali and Ubuntu version of linux.
I installed the ssh and ftp on both of them
I created some users for both
so I want to connect to ssh from kali to ubuntu, I do it but i can't connect to ftp with that user! I just connect to it with root user!
why can't I use the other user that I created before?!

and also I have to say , I can't connect to ssh and ftp from ubuntu to kali users at all!

Can someone help me?

thanks...

---

### Post by TheFu on 2017-06-22
Don't use plain FTP. Many reasons.

Don't use root directly either. That's against the normal Ubuntu setup.

Use sftp.  The openssh-server enables ssh, scp, and sftp.

Also, you probably shouldn't use Kali outside of penetration testing. It is not a secure desktop.

---

### Post by pink-hat on 2017-06-22
I don't want to use user root , I just tested it and understood that work only with root.
Also I use openssh-server.

sorry I don't understand what you mean about penetration testing! Actually I am beginner.
I work with vmware workstation.

Could you tell me what should I do exactly?

Additionally I use this website : [https://www.tecmint.com/install-ftp-server-in-ubuntu/](https://www.tecmint.com/install-ftp-server-in-ubuntu/)
but I still get this error:530 permission denied.

---

### Post by TheFu on 2017-06-22
Don't use plain FTP. Use sftp:// in almost any file manager.  
You should probably purge whatever ftp-server you installed onto Ubuntu. Wouldn't want to leave it running.

If you don't know what penetration testing is, then you should probably uninstall Kali. Much safer that way.

When you are really new, it is hard to explain things because we don't have a common language. Search for the "Ubuntu Server Guide" for lots of examples/how-tos.  "Ubuntu Desktop Guide" for desktop/GUI things.  These are newby friendly, unlike me.   ;)

---

### Post by papibe on 2017-06-22
Hi pink-hat.

Could you post the content of your /etc/vsftpd.conf (you can copy paste the text)?

Regards.

---

### Post by pink-hat on 2017-06-22
> **papibe said:**
> Hi pink-hat.

Could you post the content of your /etc/vsftpd.conf (you can copy paste the text)?

Regards.

hi papibe

this is for kali :

[ATTACH=CONFIG]275733[/ATTACH]




and this is for ubuntu:

[ATTACH=CONFIG]275734[/ATTACH]

and the other lines are comment.

thanks.

---

### Post by pink-hat on 2017-06-22
> **TheFu said:**
> Don't use plain FTP. Use sftp:// in almost any file manager.  
You should probably purge whatever ftp-server you installed onto Ubuntu. Wouldn't want to leave it running.

If you don't know what penetration testing is, then you should probably uninstall Kali. Much safer that way.

When you are really new, it is hard to explain things because we don't have a common language. Search for the "Ubuntu Server Guide" for lots of examples/how-tos.  "Ubuntu Desktop Guide" for desktop/GUI things.  These are newby friendly, unlike me.   ;)



thanks TheFu.

---

### Post by TheFu on 2017-06-22
Text, not images, are preferred here for many reasons. People pay by the bit sometimes.
Did the file manager URL work?

---

### Post by pink-hat on 2017-06-22
> **TheFu said:**
> Text, not images, are preferred here for many reasons. People pay by the bit sometimes.
Did the file manager URL work?


actually I have windows and I run kali and linux in vmware, so I can't copy text from it and past it to my computer.

about the ftp...
No! I don't really get it.

[COLOR=#000000][I]" Use sftp:// in almost any file manager. "

how can I do it?[/I][/COLOR]

---

### Post by pink-hat on 2017-06-22
I search for that topics and I got something that helped me.

I use visudo and changed the user privilege , add this line under # user privilege specification
"myuser" ALL=(ALL:ALL) ALL

and also changed Configuring the SSH server, change the port 22 into 22500 (for my Kali)

Now I can connect to ftp and ssh from kali to ubuntu and vice versa. (actually before that I can just connect to ftp and ssh from kali to ubuntu but now I can connect to ssh from ubuntu to kali with new port)

also I can connect to ssh from both with new users that I created them.
but I can't connect to ftp from these users!
I get "530 permission denied" error yet.

---

### Post by TheFu on 2017-06-22
**FTP != sftp**

Don't use the GUI in vmware. Use putty.  You can redirect output into a file, right?  virtualbox lets you copy/paste text through a shared clipboard. I'd be surprised of all the vmware tools (there are 6+ of them) couldn't do the same.

So ... load up putty.  Use pscp to copy files between Windows and Linux.  Or use WinSCP - that's a drag-n-drop GUI on Windows.
On Linux, pretty much any file manager supports ssh:// or scp:// or sftp:// in the URL field.  It works just like http:// does.   So you need to put in the correct hostname or IP address if you haven't setup name resolution.  There are many things that you just don't have the proper background.  

I assume you've been warped by Microsoft. That makes it hard to explain things.  IP networking doesn't broadcast "I'm here, I'm here" like Windows CIFS shares do.  Windows only does it for CIFS file storage, not for anything else.

Do you understand that plain FTP should have died in 1995 with telnet?
sftp is the secure replacement that is supported on every platform I know with an IP stack. Unix systems get sftp when they load openssh-server. ssh, sftp, scp all work over the same port by default. That makes it much more firewall friendly.

[Stop using plain FTP]("http://blog.jdpfu.com/2011/07/10/why-you-need-to-stop-using-ftp").
[https://askubuntu.com/questions/349873/use-connect-to-server-to-connect-to-sftp](https://askubuntu.com/questions/349873/use-connect-to-server-to-connect-to-sftp) - guide to using a file manager with sftp.

Don't know what changing the port has to do with anything.  Use bridged networking, not NAT for the VMs.

---

### Post by papibe on 2017-06-22
Thanks.

On the Ubuntu machine:

Add these 2 options to the config file:
```
userlist_deny=NO
userlist_file=/etc/vsftpd.allowed_users
```
Now only the user listed on the /etc/vsftpd.allowed_users file are allow to ftp. Add the username you want to allow to ftp, and restart the service:
```
sudo  systemctl restart vsftpd
```
Hope it helps. Let us know how it goes.
Regards.

---

### Post by pink-hat on 2017-06-23
> **TheFu said:**
> **FTP != sftp**

Don't use the GUI in vmware. Use putty.  You can redirect output into a file, right?  virtualbox lets you copy/paste text through a shared clipboard. I'd be surprised of all the vmware tools (there are 6+ of them) couldn't do the same.

So ... load up putty.  Use pscp to copy files between Windows and Linux.  Or use WinSCP - that's a drag-n-drop GUI on Windows.
On Linux, pretty much any file manager supports ssh:// or scp:// or sftp:// in the URL field.  It works just like http:// does.   So you need to put in the correct hostname or IP address if you haven't setup name resolution.  There are many things that you just don't have the proper background.  

I assume you've been warped by Microsoft. That makes it hard to explain things.  IP networking doesn't broadcast "I'm here, I'm here" like Windows CIFS shares do.  Windows only does it for CIFS file storage, not for anything else.

Do you understand that plain FTP should have died in 1995 with telnet?
sftp is the secure replacement that is supported on every platform I know with an IP stack. Unix systems get sftp when they load openssh-server. ssh, sftp, scp all work over the same port by default. That makes it much more firewall friendly.

[Stop using plain FTP]("http://blog.jdpfu.com/2011/07/10/why-you-need-to-stop-using-ftp").
[https://askubuntu.com/questions/349873/use-connect-to-server-to-connect-to-sftp](https://askubuntu.com/questions/349873/use-connect-to-server-to-connect-to-sftp) - guide to using a file manager with sftp.

Don't know what changing the port has to do with anything.  Use bridged networking, not NAT for the VMs.


thanks TheFu

I know about the sftp but a little! 
this way was not work for me.
[https://askubuntu.com/questions/349873/use-connect-to-server-to-connect-to-sftp](https://askubuntu.com/questions/349873/use-connect-to-server-to-connect-to-sftp)

I just want to test some example with terminal not in GUI.
Could you give me a link for installing a sftp in terminal mode?

---

### Post by pink-hat on 2017-06-23
> **papibe said:**
> Thanks.

On the Ubuntu machine:

Add these 2 options to the config file:
```
userlist_deny=NO
userlist_file=/etc/vsftpd.allowed_users
```
Now only the user listed on the /etc/vsftpd.allowed_users file are allow to ftp. Add the username you want to allow to ftp, and restart the service:
```
sudo  systemctl restart vsftpd
```
Hope it helps. Let us know how it goes.
Regards.

That was great!
thanks papibe

Now I can connect to new Ubuntu user from Kali with ftp.
but I still have a problem with connecting to Kali user from Ubuntu!
I do the same work for Kali but it's not working.
I get this error after entering password for my Kali user: "530 Login incorrect"

---

### Post by TheFu on 2017-06-23
Always use lowercase for all logins. DO NOT mix case.  Unix is usually case sensitive, but for logins mixed case is bad. Very bad.

[http://blog.jdpfu.com/2015/08/17/troubleshooting-ssh-connections](http://blog.jdpfu.com/2015/08/17/troubleshooting-ssh-connections) - sftp uses ssh. Get ssh working.
To my knowledge, sftp is installed at the same time as ssh and scp.  I've never had to install it separately.

[B]$ sftp userid@IP
[/B] is the general form.  If you are using non-standard ports, then you'll need to look up the option for that.  The manpages have all the options spelled out.  I use the ~/.ssh/config file to hide lots of details from me - like which port is used or which userid is used for a specific connection.

If you want to learn Linux, starting from the beginning is a good idea before moving to more complex tasks. The learning curve is steep. Skipping to the middle of the book isn't the best method and leads to lots of frustration over simple things that are part of the Unix philosophy and assumed knowledge.  As an example, setting up ssh/scp/sftp is pretty bonehead if the defaults are used and non-funky network is used.

* install openssh-server
* use any client to connect (install ssh)
It "just works", provided nothing odd happened.  I can't tell what odd things you have, but guess it appears
a) you aren't using normal networking.  NAT or host-only is not normal.  If your VMs used bridged networking, then there wouldn't be this issue.
b) Mixed case logins - They really shouldn't be accepted. ALWAYS use lowercase.
c) Kali. Actually, we aren't supposed to help with Kali here. It can be used for illegal purposes. I'm actually surprised that the thread wasn't closed due to it.

When you say something doesn't work, but don't provide more clear details, it is hard to help. Taking an error message and useing google is a common way to find a solution. "ftp 530 login incorrect" found this:
[https://askubuntu.com/questions/413677/vsftpd-530-login-incorrect](https://askubuntu.com/questions/413677/vsftpd-530-login-incorrect)

If you care about security at all, then plain FTP shouldn't be used.

---

### Post by pink-hat on 2017-06-23
> **TheFu said:**
> Always use lowercase for all logins. DO NOT mix case.  Unix is usually case sensitive, but for logins mixed case is bad. Very bad.

[http://blog.jdpfu.com/2015/08/17/troubleshooting-ssh-connections](http://blog.jdpfu.com/2015/08/17/troubleshooting-ssh-connections) - sftp uses ssh. Get ssh working.
To my knowledge, sftp is installed at the same time as ssh and scp.  I've never had to install it separately.

[B]$ sftp userid@IP
[/B] is the general form.  If you are using non-standard ports, then you'll need to look up the option for that.  The manpages have all the options spelled out.  I use the ~/.ssh/config file to hide lots of details from me - like which port is used or which userid is used for a specific connection.

If you want to learn Linux, starting from the beginning is a good idea before moving to more complex tasks. The learning curve is steep. Skipping to the middle of the book isn't the best method and leads to lots of frustration over simple things that are part of the Unix philosophy and assumed knowledge.  As an example, setting up ssh/scp/sftp is pretty bonehead if the defaults are used and non-funky network is used.

* install openssh-server
* use any client to connect (install ssh)
It "just works", provided nothing odd happened.  I can't tell what odd things you have, but guess it appears
a) you aren't using normal networking.  NAT or host-only is not normal.  If your VMs used bridged networking, then there wouldn't be this issue.
b) Mixed case logins - They really shouldn't be accepted. ALWAYS use lowercase.
c) Kali. Actually, we aren't supposed to help with Kali here. It can be used for illegal purposes. I'm actually surprised that the thread wasn't closed due to it.

When you say something doesn't work, but don't provide more clear details, it is hard to help. Taking an error message and useing google is a common way to find a solution. "ftp 530 login incorrect" found this:
[https://askubuntu.com/questions/413677/vsftpd-530-login-incorrect](https://askubuntu.com/questions/413677/vsftpd-530-login-incorrect)

If you care about security at all, then plain FTP shouldn't be used.


Thanks TheFu
It's working ^_^

actually I use a and b options that you said, before.
I know I have to change in sftp for security reason, but now I just do some project for my university and I think this things for 3-4 training movies ,are not important.
But you're right. I want to learn lots of things in security field and also I want to continue my education in "information security" in master.
So I just want to start learning this kind of things , and choose this subject for my university project.

thank you for your helping.

---

### Post by papibe on 2017-06-23
> **pink-hat said:**
> Now I can connect to new Ubuntu user from Kali with ftp.
Great! :-)

> **pink-hat said:**
> I still have a problem with connecting to Kali user from Ubuntu!
I do the same work for Kali but it's not working.
I can't help you there. I'd recommend going through Kali support channels (forum, irc, etc).

As far as I can tell, Kali is a very narrow purpose distribution, so IMHO it is **NOT** a good platform for general Linux learning. I recommend Debian is you have the option to choose from.

Regards.

---

### Post by oldos2er on 2017-06-23
> **pink-hat said:**
> sorry I don't understand what you mean about penetration testing! Actually I am beginner.


Why oh why did you install Kali (rhetorical question)? Did you see this on [https://docs.kali.org/introduction/should-i-use-kali-linux](https://docs.kali.org/introduction/should-i-use-kali-linux) ?

*As the distribution’s developers, you might expect us to recommend that  everyone should be using Kali Linux. The fact of the matter is, however,  that Kali is a Linux distribution specifically geared towards  professional penetration testers and security specialists, and given its  unique nature, it is **NOT** a recommended distribution if  you’re unfamiliar with Linux or are looking for a general-purpose Linux  desktop distribution for development, web design, gaming, etc.*

---

### Post by pink-hat on 2017-06-23
> **papibe said:**
> Great! :-)


I can't help you there. I'd recommend going through Kali support channels (forum, irc, etc).

As far as I can tell, Kali is a very narrow purpose distribution, so IMHO it is **NOT** a good platform for general Linux learning. I recommend Debian is you have the option to choose from.

Regards.



Thanks alot papibe.
I don't have any problem anymore!
I could fix it with your helping.

---

### Post by pink-hat on 2017-06-23
> **oldos2er said:**
> Why oh why did you install Kali (rhetorical question)? Did you see this on [https://docs.kali.org/introduction/should-i-use-kali-linux](https://docs.kali.org/introduction/should-i-use-kali-linux) ?

*As the distribution’s developers, you might expect us to recommend that  everyone should be using Kali Linux. The fact of the matter is, however,  that Kali is a Linux distribution specifically geared towards  professional penetration testers and security specialists, and given its  unique nature, it is **NOT** a recommended distribution if  you’re unfamiliar with Linux or are looking for a general-purpose Linux  desktop distribution for development, web design, gaming, etc.*


Hello oldos2er
I didn't know about Kali ! 
I just wanted to test some rules of iptables and snort, and I heard about some distribution of Linux, So I installed Kali and Ubuntu and I work with both of them!
Thanks for your attention.

---

### Post by TheFu on 2017-06-25
The things we write here are for your benefit. There is a reason for every line. If you don't understand a specific line, please ask.  Please review post #2 above.

---

