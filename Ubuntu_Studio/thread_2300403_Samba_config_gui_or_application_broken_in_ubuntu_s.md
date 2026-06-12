---
title: "Samba config gui or application broken in ubuntu studio 15.10"
date: 2015-10-25
forum: Ubuntu Studio
---

### Post by jmarkus on 2015-10-25
Hi, I had samba running, and configured in 14.04. Ran the upgrade to 15.10, and most applications survived. However, the Samba configuration gui/app is now broken. I can no longer see any of the shared drives of this machine from my other computers, but I can see other samba shares of other linux computers, and NAS from this computer. When I go to launch the Samba app it asks for my password, and then nothing. No error message. So, I can not configure the shares. I have tried un-installing and installing, and literally a half dozen other variations of the same - all with no effect. Is there any source of information, or bug fixes for this issue? Is there any alternative to Samba?

---

### Post by jmarkus on 2015-10-25
I'm getting this response through the terminal now

xw6600:~$ gksu system-config-samba
  File "/usr/sbin/system-config-samba", line 45, in <module>
    mainWindow.MainWindow(debug_flag)
  File "/usr/share/system-config-samba/mainWindow.py", line 82, in __init__
    self.samba_data = sambaParser.SambaParser(self)
  File "/usr/share/system-config-samba/sambaParser.py", line 185, in __init__
    self.parseFile ()
  File "/usr/share/system-config-samba/sambaParser.py", line 225, in parseFile
    token = self.createToken (line, section) 
  File "/usr/share/system-config-samba/sambaParser.py", line 310, in createToken
    name, value = line.split ("=", 1)
ValueError: need more than 1 value to unpack


Odd thing is that there is only 281 lines in the smb.conf file (both in etc and usr)- I really don't know how to trouble shoot this one.
Any ideas?

---

### Post by jmarkus on 2015-10-30
I wiped the hard drive clean, because I have a laptop with 15.10 as well - and samba works fine. After the clean install I got a difference gksu error. 
After this set of terminal commands I was right back to square one. Samba would ask for the admin password, and then would do nothing.

These terminal commands got rid of the gksu orphaned child error

sudo apt-get install gksu
sudo apt-get install samba samba-common
sudo apt-get install system-config-samba cifs-utils

 
This terminal command fixed the non-responsive gui/app for Samba. 
sudo touch /etc/libuser.conf

I don't know why samba was fine on my laptop, but broken on the desktop - both from clean installs. However,
the above did fix it for me. Hope it helps someone else.

---

### Post by lubo2 on 2016-09-27
Awesome find jmarkus!

This fixed the problem for me in Xubuntu 16.04.1 64 bit.

This should be fixed upstream if possible, I'm off to look into filing bugs.

One to make cifs-utils (and maybe gksu?) a dependency of system-config-samba, since it was not installed when system-config-samba was. And one to make the cifs-utils package do sudo touch /etc/libuser.conf so it doesn't error out.

---

### Post by QIII on 2016-09-27
Rest in Peace, dear thread.

---

