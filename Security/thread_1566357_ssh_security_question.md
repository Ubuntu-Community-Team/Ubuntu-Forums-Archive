---
title: "ssh security question"
date: 2010-09-02
forum: Security
---

### Post by Tamale on 2010-09-02
I'd like to add a user to my server that will only have access to a mount point over sshfs.  Is there any way I can provide them this access without actually giving them permission to open a terminal on my server?

I tried /bin/false and /sbin/nologin already, but /bin/false didn't allow the mount point to be made and /sbin/nologin prevented a login completely (also stopped the mount point from working).

Thanks!

---

### Post by scorp123 on 2010-09-02
Google for "scponly" ... that way users can use SFTP and SCP (e.g. via clients such as gftp, FileZilla, WinSCP, or plain 'scp' shell commands) but they can't login via SSH. Maybe this is what you want?

There was a similar thread recently. See here:
[http://ubuntuforums.org/showthread.php?p=9789237#post9789237](http://ubuntuforums.org/showthread.php?p=9789237#post9789237)

---

### Post by Tamale on 2010-09-02
that would work fine assuming scp is how sshfs works.. but I'm not sure this is the case. I guess I could try, but I figured there was a better built-in way to do this.. 

essentially, I want ssh to WORK, but then no interactive-shell access to actually be permitted.

---

### Post by bodhi.zazen on 2010-09-02
I suggest you use keys and what are called "forced commands"

[http://binblog.info/2008/10/20/openssh-going-flexible-with-forced-commands/](http://binblog.info/2008/10/20/openssh-going-flexible-with-forced-commands/)

[http://oreilly.com/catalog/sshtdg/chapter/ch08.html](http://oreilly.com/catalog/sshtdg/chapter/ch08.html)

You can set things such as no X forwarding, no port forwarding, etc in the key, this keeps ssh from abuse.

---

### Post by scorp123 on 2010-09-02
> **Tamale said:**
> that would work fine assuming scp is how sshfs works..  No it isn't. But then again SSHFS isn't very stable anyway. Hence why I suggested to use SCP or SFTP clients and limit your users on that.

If you just want your users to have access to a certain folder but without the ability to login you might just as well also use NFS or SAMBA shares :D  (and don't forget to tweak their accounts so they can't login).

---

### Post by Tamale on 2010-09-02
> **scorp123 said:**
> No it isn't. But then again SSHFS isn't very stable anyway. Hence why I suggested to use SCP or SFTP clients and limit your users on that.

If you just want your users to have access to a certain folder but without the ability to login you might just as well also use NFS or SAMBA shares :D  (and don't forget to tweak their accounts so they can't login).

I'm limited to sshfs because of the ports I can forward in my particular situation.

---

### Post by scorp123 on 2010-09-02
> **Tamale said:**
> I'm limited to sshfs because of the ports I can forward in my particular situation. And use a VPN is not possible? Read here:

[http://ubuntuforums.org/showthread.php?p=9792233#post9792233](http://ubuntuforums.org/showthread.php?p=9792233#post9792233)

Remobo works tip top for Windows, Linux and Mac. No knowledge required, you just start it, you login ... that's it. Port-forwarding and what not isn't required either. And I tested it by logging into two of my systems that are at two different office locations + one system at home ... and it worked, no matter how many restrictive firewalls were between them.

My idea here is that you and whoever needs to connect to you login into Remobo and no matter what their OS is, you would be able to use whatever protocol is necessary to share your files securely (Remobo supposedly uses AES-256 encryption for its traffic).

With this you'd have more options in regards to what you want to use and how you want to share your files.

Just my opinion.

BTW: Each Remobo user gets a new 7.x.x.x IP each time they login. So far so bad. But the good news is that Remobo also comes with a "dynamic DNS" (aka 'DynDNS') service built-in, e.g. each host can always be reached via its hostname or location name (= whatever you entered into the "Location" field when you created the account on your system -- I used hostnames there):

[B]<hostname>.<username>.remobo.com
<location>.<username>.remobo.com[/B]

So let's say I want to SSH into my MacBook Pro which has the hostname "shiny", I'd fire up Remobo and then simply SSH into it:
```
ssh shiny.scorp123.remobo.com
```

... and I don't have to bother the firewall guy in our company with port-forwardings and what not.

I didn't test other network protocols so far (I am 100% happy with SSH working between my systems) but according to the forums BitTorrent and Windows file sharing (= SAMBA in Linux speak) seems to work too.

Maybe this is a solution for you.... ?

---

