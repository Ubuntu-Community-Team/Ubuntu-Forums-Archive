---
title: "Ubantu in virtual box"
date: 2008-09-29
forum: Virtualisation
---

### Post by sai_viswanath on 2008-09-29
HI
I'm using ubantu, running in virtual environment of windows xp(SP2).
But I'm unable to share the folders of windows xp with ubantu.
Help me.

---

### Post by Sycron on 2008-09-29
Can you be more specific ? We can't help you if you don't say more about your situation.

Thank you.

---

### Post by thenetduck on 2008-09-29
I ran into this problem on a while back. I haven't tested it sense. My problem (this might help clarify his question) was I created a shared folder and would try to mount my VB's shared folder inside of windows via MS-DOS Prompt but it would not mount or reconize the shared folder. I don't know if this is a VB tools issue or OS specific. 

I would read what VB's Docs has to say about it. They are usually really good (from my experience) and specific to Ubuntu and Suse

---

### Post by bodhi.zazen on 2008-09-29
The issue is that you are trying to share things with two isolated computers, or at leaset lest start thinking of them in those terms.

IMO the solution is to learn a network protocol. Network protocols work just as well as virtualbox shared folders and if you learn network protocols you are learning something which has broader applications.

You can share folders with samba, NFS, FTP, ssh (scp), or apache.

Probably what you want is Samba. Samba *should* work out of the box.

[http://ubuntuforums.org/showpost.php?p=5400935&postcount=11](http://ubuntuforums.org/showpost.php?p=5400935&postcount=11)

[https://wiki.ubuntu.com/ComprehensiveSambaGuide](https://wiki.ubuntu.com/ComprehensiveSambaGuide)

[https://help.ubuntu.com/community/SettingUpSamba](https://help.ubuntu.com/community/SettingUpSamba)

If you wish an alternate to samba I suggest SSH. Install a ssh server on Ubuntu and use Putty / Winscp on windows.

[http://winscp.net/eng/docs/screenshots](http://winscp.net/eng/docs/screenshots)

[https://help.ubuntu.com/community/SSHHowto](https://help.ubuntu.com/community/SSHHowto)

---

