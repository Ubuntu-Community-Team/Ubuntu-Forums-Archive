---
title: "Installing SSH Server"
date: 2006-12-02
forum: Server Platforms
---

### Post by deadfolk on 2006-12-02
Hi all,

Total Linux n00b here. ;) 

I need to install an SSH server on Edgy - I'm assuming OpenSSH is what I need to use.  My problem is that Synaptic does not show anything which is obviously OpenSSH or any kind of SSH server.  There are plenty of clients listed (PuTTY, etc.).

My sources.list has nothing commented out, and I have done an update.

Can anyone please point me in the right direction?

Thanks,

DF

---

### Post by kjacks on 2006-12-02
sudo apt-get install openssh-server

Does that work for you?

---

### Post by deadfolk on 2006-12-02
That worked perfectly - thanks for the quick reply!:) 

I had assumed that apt-get and synaptic used the same list.  Is that not the case?  Otherwise, why would it not have shown up in synaptic?

Also, would you mind telling me where you can find a list of packages to install with apt-get?

Thanks again.

---

### Post by chrisfay on 2006-12-02
[http://packages.ubuntu.com/](http://packages.ubuntu.com/)

---

### Post by deadfolk on 2006-12-02
Perfect - thank you.

Wow.  It's true what they say about the Ubuntu community!  Never had such quick and helpful replies on a forum before.

---

