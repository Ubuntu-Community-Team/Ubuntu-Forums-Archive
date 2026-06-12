---
title: "sudoers error"
date: 2006-03-16
forum: Ubuntu Backports
---

### Post by Bunro on 2006-03-16
I followed this tread and unfortunately I can not get to edit /etc/sudoers 
“ >>> sudoers file: syntax error, line 24 <<<
sudo: parse error in /etc/sudoers near line 24

[http://www.ubuntuforum.org/showthread.php?p=829992#post829992](http://www.ubuntuforum.org/showthread.php?p=829992#post829992)

[sudo gedit /etc/sudoers

add in the bottum of the page:
<insert your username> ALL= NOPASSWD: /usr/sbin/firestarter
Save it.

Now go to System ---> Preferences ---> Sessions
Switch to Startup Prgrams tab and click add button.
In the command box: sudo firestarter --start-hidden
and order box: 50]

I did the installation and I followed the steps as described above. But added the lines
<insert your username> ALL= NOPASSWD: /usr/sbin/firestarter at the bottom of the page with sudo gedit /etc/sudoers.

With a restart it is not working.
When I try to edit egain the file via sudo gedit /etc/sudoers
I am getting the following error:
“ >>> sudoers file: syntax error, line 24 <<<
sudo: parse error in /etc/sudoers near line 24

I can not get in to the sudoers file.

How can I solve this problem?

Regards, Robert

Ps. I tried to enter synaptic to reinstall firestarter but I am getting the following error:
[Failed to run /usr/sbin/synaptic as user root: Child terminated with 1 status.]

---

### Post by bscbrit on 2006-03-16
Restart the computer in recovery mode and change the file back to its original values, or find line 24 and correct whatever is wrong.  Recovery mode will automatically set you up as 'root'.

---

### Post by Bunro on 2006-03-16
Thanks BSCBRIT,

Problem solved!

Regards, Robert

---

### Post by sunshine on 2006-03-27
I'm running into basically the same problem. However, everytime I try to restart in recovery mode, it will not accept my root password. It tells me "incorrect login" and will not continue. Is there another way to access /etc/sudoers?

---

### Post by devzman on 2008-06-06
You can allways access the disc by using a Linux boot-disc. Use this to mount the filesystem, and change the root-password or change the contents of /etc/sudoers. Having physical access to the machine allows for this. If you dont want this, you should install LUKS. But if you loose your LUKS password, your data is lost forever.

---

### Post by hzj1556 on 2009-02-19
> **Bunro said:**
> Thanks BSCBRIT,

Problem solved!

Regards, Robert
I met this problem also ,you said your problem has been solved ,can you tell me how to solve the problem 
email:hzj1556@sina.com 
thanks

---

