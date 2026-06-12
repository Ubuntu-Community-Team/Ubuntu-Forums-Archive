---
title: "Jerky Txfer of files over NFS. Server sticks unless key pressed??"
date: 2008-07-27
forum: Server Platforms
---

### Post by HarryCoul on 2008-07-27
I have a ubuntu 8.04 server with a couple of NFS exports.

Recently I've noticed that when copying large files, or doing things such as playing media on a seperate machine over NFS, the transfer appears to periodically block ( or at least slow right down ).

This seems to of been getting worse lately but I can't swear to that.

Today I noticed a really strange occurance.

On a client machine play a AVI file which is on a NFS mount from the server. Every few seconds the video locks up, sometimes for 1/2 a second, sometimes several seconds. (using mplayer on gentoo x64 - but that shouldn't matter ).

Now I also at the time had a SSH session running connecting the client to the server. Each time the video glitched if I sent any character over the SSH ( doesn't matter what ) the video spooled on happily for a few more seconds.

So right now it appears that NFS works fine so long as I keep typing into a console on the server!

Any ideas guys?

---

