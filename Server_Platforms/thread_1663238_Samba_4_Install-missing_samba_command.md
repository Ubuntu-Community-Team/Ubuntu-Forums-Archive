---
title: "Samba 4 Install-missing samba command"
date: 2011-01-09
forum: Server Platforms
---

### Post by edthetoad on 2011-01-09
After I install samba 4 on my computer I cannot use the command samba.  It tells me that it cannot find the command.  To install I used the commands sudo ./configure, sudo make, and sudo make install.  Is there some other command I must use to completely install samba?

---

### Post by CharlesA on 2011-01-09
Samba 4 is still in alpha as far as I know. Is there a specific reason you are wanting to use it?

---

### Post by edthetoad on 2011-01-09
I am using samba 4 because I have already have a working samba 3 primary domain controller and I want to be able to use active directory and not have an NT4 domain

---

### Post by CharlesA on 2011-01-09
Ah I see. I can't really help you there.

There might be some info on Samba4, but I don't know how reliable it is considering it's still in Alpha.

---

### Post by bmullan on 2011-02-24
> **edthetoad said:**
> After I install samba 4 on my computer I cannot use the command samba.  It tells me that it cannot find the command.  To install I used the commands sudo ./configure, sudo make, and sudo make install.  Is there some other command I must use to completely install samba?

Depending on whether you installed samba4 using synaptic for did a "git" pull of the latest & then built it you will find the samba executable in one of two places

if you used git then it probably created a samba-master directory from wherever you issued the git from.

./samba-master/source4

or

/usr/local/sbin/samba
 
but you can find where its at by doing

sudo find / -name samba -print

samba and all the samba tools are in the same directory I believe.

---

### Post by rlmanni on 2011-03-13
> **edthetoad said:**
> After I install samba 4 on my computer I cannot use the command samba.  It tells me that it cannot find the command.  To install I used the commands sudo ./configure, sudo make, and sudo make install.  Is there some other command I must use to completely install samba?

I ran into the same problem. After a few hours searching I found this : [http://samba.2283325.n4.nabble.com/Samba4-start-error-td3326610.html](http://samba.2283325.n4.nabble.com/Samba4-start-error-td3326610.html)

Long story short, if you installed in the default directory, you can start samba this way:

```
sudo /usr/local/samba/sbin/samba
```You will need to add that directory to your PATH in order to call just 'samba' from the command line.  If you check out the Samba4/HOWTO pages, there is one for Ubuntu 9.04 that details creating an init.d script as well

Edit:

Also wanted to note that from everything I've read about samba4 is that its fairly reliable. It seems to be missing print server support, but other than that acts like a true AD even updated with the schema for Server 2008

---

