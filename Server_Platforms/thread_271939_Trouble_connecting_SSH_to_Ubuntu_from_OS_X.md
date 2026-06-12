---
title: "Trouble connecting SSH to Ubuntu from OS X"
date: 2006-10-05
forum: Server Platforms
---

### Post by gdog05 on 2006-10-05
Hi everyone.

I'm very new to SSH, and I am having a login problem. I am using a new Mac with OS X.4.8, and trying to SSH into my Ubuntu 6.06 server. I got this to work a couple of weeks ago, by luck. In OS X Terminal, using:{ sudo ssh username@192.168.1.111 }  it allowed me access the machine. I just did a reinstall, set up SSH and networking, and it treats me like a foreigner. I get this error:

@    WARNING: REMOTE HOST IDENTIFICATION HAS CHANGED!     @
IT IS POSSIBLE THAT SOMEONE IS DOING SOMETHING NASTY!
Someone could be eavesdropping on you right now (man-in-the-middle attack)!
It is also possible that the RSA host key has just been changed.
The fingerprint for the RSA key sent by the remote host is
xx:xx:xx:xx:xx:xx:xx:xx:xx:xx:xx:xx:xx:xx:xx:xx.
Please contact your system administrator.
Add correct host key in /var/root/.ssh/known_hosts to get rid of this message.
Offending key in /var/root/.ssh/known_hosts:1
RSA host key for 192.168.1.111 has changed and you have requested strict checking.
Host key verification failed.

It seems to me that my .ssh/known_hosts file has the info from before the format, but won't accept me to add to the user list. I was able to log in fine from an OS X machine that I had not logged in from before. It asked if I wanted to update the SSH to allow the machine kind of thing. Is there something really standard that I'm not doing? Like I say, I'm new to SSH, but it seems like I'm doing everything right. Anyone's input is appreciated. Thanks.

---

### Post by skymt on 2006-10-05
When you install ssh, it generates a key (really, really long number) that identifies that computer. When you re-installed Ubuntu, it generated a different key. Now your Mac sees a different key with the same address and says, "That's not right. It may be a different computer with the same address!" It basically is.

The solution is to delete your ~/.ssh/known_hosts. When you next try to ssh into Ubuntu from your Mac, it will ask you if you want to add Ubuntu to your known_hosts. Say yes, and everything will work as normal.

---

### Post by gdog05 on 2006-10-05
That's awesome. That is exactly what I was looking for. OS X will not show that particular file, though. I imagine I can access it through the terminal, but I'm not good enough with the commands. How would I back up the known_hosts and then delete? Thanks for your help.

---

### Post by skymt on 2006-10-05
> **gdog05 said:**
> That's awesome. That is exactly what I was looking for. OS X will not show that particular file, though. I imagine I can access it through the terminal, but I'm not good enough with the commands. How would I back up the known_hosts and then delete? Thanks for your help.

```
cd ~/.ssh
cp known_hosts known_hosts.backup
rm known_hosts
```

Here's a little bonus tip for you: to get to a hidden folder in the Mac Finder, use Go > Go to Folder. Then enter the path to the folder ("~/.ssh", in this case) and hit Go.

---

### Post by gdog05 on 2006-10-05
You are a wealth of information, thank you very much. I can't really find the source folder for the var/root/.ssh, though. Any suggestions on how to find it?

---

### Post by gdog05 on 2006-10-05
After a bit of searching, as always, I found a workaround. In case anyone stumbles in with the same question, here's what I did. Open terminal and type:{ defaults write com.apple.Finder AppleShowAllFiles YES }

This will show all the hidden files and folders. You can then find the var/root folder and change permissions if need be. I just edited the var/root/.ssh/known_hosts file. I killed out all the gibberish key info. Then, when I try to SSH again it asked me if I wanted to add the information to the known_hosts list just like I wanted. To turn off show all files, type NO instead of YES in the code above. Thanks again for your help skymt.

---

