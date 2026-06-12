---
title: "Best way to organize my info, apache"
date: 2009-06-29
forum: The Cafe
---

### Post by whitethorn on 2009-06-29
Hi,

So I'm pretty much looking for a better way to organize my info.  Pretty much the info I have are stuff I found here on the forums or needed sometime or other.  At the moment I'm using Basket Notepads, I wouldn't mind having something I could view when I'm not sitting at my computer (ssh works just it's pretty slow).  I was thinking something like a doku wiki running on my apache server.  Ne1 have a couple good ideas?

---

### Post by mobilediesel on 2009-06-29
> **whitethorn said:**
> Hi,

So I'm pretty much looking for a better way to organize my info.  Pretty much the info I have are stuff I found here on the forums or needed sometime or other.  At the moment I'm using Basket Notepads, I wouldn't mind having something I could view when I'm not sitting at my computer (ssh works just it's pretty slow).  I was thinking something like a doku wiki running on my apache server.  Ne1 have a couple good ideas?

You could try [Tiddlywiki]("http://tiddlywiki.org"). It's mostly for local use but there is a plugin so you can update it remotely. Then there's [Mediawiki]("http://www.mediawiki.org/"), which is what Wikipedia uses.

---

### Post by tgalati4 on 2009-06-29
I use zim for my notes.  You can run it remotely on several machines at once.

---

### Post by mobilediesel on 2009-06-29
> **tgalati4 said:**
> I use zim for my notes.  You can run it remotely on several machines at once.

I'm checking that out now! It just might replace Tiddlywiki on my system.
***I've been playing with Zim for a few minutes here. I like how they purposely set it up so you don't HAVE to rely on their program for quick edits.***

---

### Post by tgalati4 on 2009-06-30
What's neat about zim:

You install it on a desktop/server (a machine that's on 24-7).

Remotely log in using X-forwarding:

ssh -2 -Y user@remotemachine

remotemachine$ zim &

You can run it on several machines simultaneously.  Updates to notes magically appear on all machines since it's hosted on only one central machine.  Don't know about simultaneous updates and file-locking.  May not be robust enough for multiuser environment.

File format is text-based, simple, and easy to back up.

I used tiddlywiki for a while, but it seemed cumbersome.

---

### Post by whitethorn on 2009-06-30
Cool, I'll give Zim a try.

---

### Post by mobilediesel on 2009-06-30
> **tgalati4 said:**
> What's neat about zim:
You install it on a desktop/server (a machine that's on 24-7).
Remotely log in using X-forwarding:
ssh -2 -Y user@remotemachine
remotemachine$ zim &
You can run it on several machines simultaneously.  Updates to notes magically appear on all machines since it's hosted on only one central machine.  Don't know about simultaneous updates and file-locking.  May not be robust enough for multiuser environment.

File format is text-based, simple, and easy to back up.

I used tiddlywiki for a while, but it seemed cumbersome.

I don't need to run it on more than one machine at a time but possibly in the future.

Tiddlywiki is a bit cumbersome but easier to install and maintain than mediawiki since it's just one file. I'm getting ready to move all my tiddlywiki stuff to Zim now. I'm just trying to find the "export tiddler" plugin that I saw before but decided I didn't need.

*added: July 02, 2009*
Zim is very cool! I exported my Tiddlywiki using [http://www.tiddlytools.com/#ExportTiddlersPlugin](http://www.tiddlytools.com/#ExportTiddlersPlugin) and had to copy and paste stuff from the resulting file. Zim couldn't import it directly but I didn't have a ton of stuff. I also moved stuff from my Mediawiki and uninstalled that.

I played with Xpad for a bit but Zim is way more capable.

---

