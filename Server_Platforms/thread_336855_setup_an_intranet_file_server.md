---
title: "setup an intranet file server"
date: 2007-01-12
forum: Server Platforms
---

### Post by andytof47 on 2007-01-12
Hi I am just wondering how i would go about setting up a central file server - not just share a folder on a workstation????

really i want information on how to set up an intranet i think

Thanks in advance

---

### Post by Jussi Kukkonen on 2007-01-12
I believe you should be more specific. What should a "central file server" do in addition to sharing folders? You could also try to list your possible use cases if that's easier.

---

### Post by Brazen on 2007-01-12
You will use Samba.  That is what Samba does - it shares files with Windows clients (I assume you will have Windows clients).  Samba is available in the Ubuntu repositories.  There is some good starter information, if you would have just checked the Ubuntu documentation:  [https://help.ubuntu.com/6.06/ubuntu/serverguide/C/windows-networking.html](https://help.ubuntu.com/6.06/ubuntu/serverguide/C/windows-networking.html)

---

### Post by randomnumber on 2007-01-12
I just use ssh protocols. It should be more secure.

If you want access to your files on the Internet the ssh protocols work great. The only difficulty in getting a file server to work on the Internet is knowing your computers address. If you are behind a router you may want to do port forwarding. Of course that is going further than you asked. 

Another thing that ssh allows you to do is type cmds to your computer from a remote location. This is not a gui thing though.

---

### Post by echo $USER on 2007-01-12
deleted

---

### Post by Brazen on 2007-01-12
Why are you giving information on an internet file server, when the OP specifically asked for an intranet solution?

---

### Post by echo $USER on 2007-01-12
deleted

---

### Post by randomnumber on 2007-01-14
> **Brazen said:**
> Why are you giving information on an internet file server, when the OP specifically asked for an intranet solution?

It can be used both ways. I also prefer it on intranet connections. I do not like the way windows does intranet file sharing. The next question is how do you get access to your file from a remote location. I only offered it as an alternative.

---

