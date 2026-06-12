---
title: "samba+winbind+windows7 funny"
date: 2011-05-19
forum: Server Platforms
---

### Post by kopbeen on 2011-05-19
Hi there,
 
My client is running Ubuntu 9.04 server for a while now without any issues.  We use the server as a fileserver and used the samba/winbind online howtos to make the server a member server in a windows 2003 domain. (one DC only) Currently we have several Windows xp & windows 7 clients connecting to the shares, no problem.
 
One windows 7 machine 'suddenly' decided not to connect to the shares anymore, here's the symptoms:
 
1. When I type [\\servername]("file://\\servername") in Windows explorer, I get the error " The server's clock is not synchronized with the primary domain controller's clock".
 
-> I checked the time on the windows 7 wks, and it was the same as the AD server's - also did a net time /set command to make doubly sure.
 
2. Next I type [\\<ip]("file://\\<ip") address> in Windows explorer, now I get prompted for a network password. Entering valid AD usernames/passwords does not work.  As  a desperate attempt, I entered the root user and password in the 'enter network password' prompt, that immediately solved the problem. I can now see all the shares and access them. (Without anymore prompts) -  I can also now used the [\\servername]("file://\\servername") way to access the shares…  I restarted the workstation to confirm the ‘workaround’ worked and I can still access the shares.
 
Any idea why this behavior occurs? :confused: How can I prevent these new/existing windows 7 machines trying to access the samba shares?
 
thx in advance for the time + help…

---

### Post by kmortensen on 2011-05-19
I apologize for responding to a question with a question, but...

I see that you have working Samba shares for Windows/active directory clients... HOW DID YOU DO THAT?  I have a new server that is running Ubuntu 10.04 (I want it to be my file server) and I have a single domain controller (2003) with Windows 7 clients.  If you can point me to a step by step set of instructions, it would be greatly appreciated!  Sorry if I am not giving enough information about my current environment...I am a Windows Admin, and really enjoy working with linux, but am still not proficient.

Again, any help is greatly appreciated!

---

### Post by kopbeen on 2011-05-20
Hi there,
 
No problem at all...
 
I used the following article - its based on 9.04 .. but I guess it would be simillar for ver. 10.04... :)
 
[http://www.howtoforge.com/ubuntu-9.04-samba-server-integrated-with-active-directory](http://www.howtoforge.com/ubuntu-9.04-samba-server-integrated-with-active-directory)

---

### Post by kmortensen on 2011-05-20
thanks for the help! ironically, I used the same exact how to to set up my system.  I must be doing something wrong with the share creation then: I can create a share (i am using webmin, but can go command line to do this if I need to), and the share is visible to windows clients, but I cant seem to get permissions right so that certain AD groups have read only access and others have modify access.  Maybe I am putting the shares in wrong spot on the Linux box??? And truly, I havnt been able to figure out how to add domain users/groups onto the samba acl.  Again, thanks for the help, and sorry to hijack your initial thread...

---

