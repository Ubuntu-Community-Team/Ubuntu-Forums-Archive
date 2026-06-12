---
title: "Ubuntu Server - OpenSSH pausing on transfers"
date: 2008-10-26
forum: Server Platforms
---

### Post by IMSargon on 2008-10-26
Here's my setup

Fresh install of Ubuntu Server 8.10 Release Candidate (Beta did same thing, though)
Fresh install of Ubuntu Desktop 8.10 Beta

I connect from the Desktop to the Server using the "Connect to Server..." function in the menu. I navigate to my home folder and drag in a folder full of files - about 4GB in all, a complex mixture of folders, subfolders, and files of all types and sizes.

The transfer proceeds normally (perhaps a bit slower than expected?) but after a few hundred MB, it hangs. It just sits there not copying, but the transfer rate doesn't decrease and the orange bars still cycle across the stationary progress bar. Any ssh terminals I have into the server also freeze.

Nothing I can do on the client will make it go again, but here's the strange thing: if I walk over to the server and hit a key - any old key will do - it will resume the transfer, at least for a while.

It isn't apparmor, I've tried disabling that. It isn't a hardware issue of any sort, because I don't have the problem on two desktop editions of the exact same hardware. 

Now, I can live with slow if I have to, but unreliability just won't do. Can somebody explain what's going on?

---

### Post by cariboo on 2008-10-26
You have to remember release candidate, that means that it is frozen and there will be nothing new  added, there are still quite a few bugs that need to be swatted, since the release candidate was released on Thursday I've had close to 100 updates. I would check on [Launchpad]("http://bugs.launchpad.net/") to seem if someone is having similar problems. If you don't find anything submit a bug report, the devs can't fix a problem if they don't know about it.

Jim

---

