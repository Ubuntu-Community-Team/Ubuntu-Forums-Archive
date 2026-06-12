---
title: "Setting up a CVS server"
date: 2005-10-25
forum: Server Platforms
---

### Post by cwc on 2005-10-25
Howdy,

I figured this was the most appropriate forum for this question. I'd like to know what is the preferred way of setting up a CVS server in Ubuntu? I know how to set up and configure the server in general, but want to know the cleanest way to do so in Ubuntu.

I installed the cvs package through synaptic, but that by itself does not seem to make it any simpler to just start up a server. Should I go ahead and edit inetd.conf to start up cvspserver, or what?

Also, where is it recommended to actually place the repository? I planned on putting it in e.g. /home/cvs, creating a separate user for CVS, setting up the necessary permissions, etc., but would like to know if this is usually done in a different way in Ubuntu.

---

### Post by LordHunter317 on 2005-10-25
Well, first off, unless you **must** run pserver, don't.  And since you don't know how to do that, the answer to that question is no.

Use SSH to let people access your CVS server.  Create normal shell accounts for every user who needs CVS access.  If that's all they need, then use rssh to restrict them to running CVS only.

You can put the repository anywhere, but the new "standard" place is /srv/cvs.  In reality, put it wherever you like.

This is standard on any Linux, FWIW.  I personally use the same CVS policies and procedures just about everywhere.

---

### Post by cactus on 2005-10-25
If at all possible, setup subversion instead. You can even set it up with mod_svn, which allows subversion and apache to work together to bring you subversion over http (although i use https for security).

---

### Post by LordHunter317 on 2005-10-26
I prefer svn+ssh, because it's much closer to how CVS works in practice, and it doesn't require breaking your permissions structure to use Apache.

---

### Post by Vex on 2005-12-30
Hi,

I've recently upgraded a development server from an old version of Red Hat, to Ubuntu, and so far I've been very impressed with it!

However, I'm having some trouble getting my CVS server up and running. Previously under Red Hat, the CVS server was running via pserver, and ideally I'd llike to get this running again.

Is there a strong reason not to use the pserver? Because all my existing projects under CVS, and the windows machines that use the CVS are setup to connect via pserver, and I don't really want to go through changing all the 'root' files to a different connection string.

I did try using an 'ext' type connection for a test project, but that seems to require a password for each connection which is a pain.

Can someone explain how to get the cvspserver up and running in Ubuntu? Or if I really shouldn't be using that, then is it possible to get a 'ext' connection that doesn't require a password for each connection?

(Additional info: The CVS server is running on an internal network, and is only used by myself, from a windows machine, using TortoiseCVS. I do have some limited linux experience, but so far I've fail to figure out getting a cvspserver running... :) )

---

### Post by LordHunter317 on 2005-12-30
[QUOTE=Vex]Is there a strong reason not to use the pserver?[/quote]It's insecure crap, plain and simple.  It's not encrypted and has had security vulnerabilites before.  Best to use SSH and mitigate what you can.

>  Because all my existing projects under CVS, and the windows machines that use the CVS are setup to connect via pserver, and I don't really want to go through changing all the 'root' files to a different connection string.You don't.  Commit, delete, and checkout again.

> I did try using an 'ext' type connection for a test project, but that seems to require a password for each connection which is a pain.With tortoise CVS, setup an SSH public keypair and load it at boot via pagent.exe.  You'll only have to enter your password once, at login to Windows.

As for setting up pserver on Ubuntu, I've never done it, but if there's anything special to be aware of, look in /usr/share/doc/cvs.  Otherwise, it should be the same as any other platform.

---

### Post by Vex on 2006-01-01
Thanks for your comments.

I figured that the main problem with using pserver would be to do with security.

I've just spent a bit of time messing around/learning about PuttyGen and SSH keypairs and stuff, and my CVS seems to be working nicely now without having to use the pserver.

Thanks very much. :)

---

