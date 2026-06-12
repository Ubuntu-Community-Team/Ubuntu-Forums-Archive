---
title: "can't get samba file sharing to work - please check this config"
date: 2009-05-23
forum: Server Platforms
---

### Post by RobertL on 2009-05-23
I'm trying to get samba working on machine named 'black' running jaunty. The client is a Windows XP Pro machine named 'blue'. There is another WinXP machine named 'silver' (and potentially a few others). This is a small office network with no domain controller.

I got printer sharing working. IOW blue can print on a printer directly connected to black. But when blue tries to open a file share on black he gets the following message:

\\BLACK\foo is not accessible. You might not have permission to use this network resource. Contact the administrator of this server to find out if you have access permissions. The group name could not be found.

I have all the usernames and group names set to 'bob' everywhere (so far as i know). That's not what I ultimately want but I set them that way to try to get it working because so much of the documentation talks about usernames and group names without specifying which ones they are talking about. So the ubuntu directory being shared (which is "/home/bob/mysambafolder/") is owned by bob, group=bob, mode=777, the XP username is bob, the smbpasswd was enabled for bob, and the password for bob is the same on the XP and linux machines. When I start samba (sudo service samba start), and I have the 'network places' window open on the XP machine, a line pops on with the name of the share on black, so the XP machine is seeing the linux machine and some information is passing. (BTW all machines can ping each other.) The workgroup names are the same on all machines and in the global section of /etc/samba/smb.conf.

I am attaching the smb.conf file (as smb.conf.txt because of forum rules). Also log.blue as log.blue.txt. 

The log file is loaded with error messages that are not self-explanatory to someone not steeped in samba-speak. Could someone who understands samba look at this log file and tell me what's wrong in light of the context I've explained here?

One thing to note, which I presume is a bug in the error message format: several of the error messages have the last character truncated. So when its apparently looking for /var/lib/samba/usershares/foo, the error message says it can't stat /var/lib/samba/usershares/fo. This is consistent with different names that I tried (not only when the share name is 'foo'). And BTW why is it looking in that directory? I haven't mentioned that anywhere.

---

