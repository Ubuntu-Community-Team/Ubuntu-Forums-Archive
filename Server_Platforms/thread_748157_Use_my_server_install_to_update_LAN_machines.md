---
title: "Use my server install to update LAN machines?"
date: 2008-04-07
forum: Server Platforms
---

### Post by shane2peru on 2008-04-07
ok, I installed a server and am a complete noob at this server stuff!  I've become pretty Linux savvy, and enjoy learning. I have my computer (I just recently installed the server edition and installed desktop it will double as both server and desktop) then I have two other Ubuntu machines.  I keep them all up to date etc.  So when I update one machine, then I go and update the other, and the other etc.  It is a lot of double downloading.  Is there anyway with the server install that these machines can just get their updates from the download that has already been done?  I don't know if this belongs in the server threads or not, sorry if it is the wrong place.

Shane

---

### Post by jcostom on 2008-04-07
> **shane2peru said:**
> ok, I installed a server and am a complete noob at this server stuff!  I've become pretty Linux savvy, and enjoy learning. I have my computer (I just recently installed the server edition and installed desktop it will double as both server and desktop) then I have two other Ubuntu machines.  I keep them all up to date etc.  So when I update one machine, then I go and update the other, and the other etc.  It is a lot of double downloading.  Is there anyway with the server install that these machines can just get their updates from the download that has already been done?  I don't know if this belongs in the server threads or not, sorry if it is the wrong place.

Shane

If you'd like to create a local mirror, it's not terribly hard..

If you want to mirror the whole Ubuntu archive (unlikely), rsync is the way to go, since it grabs everything.  That's a couple of hundred gigs.

[https://help.ubuntu.com/community/Rsyncmirror](https://help.ubuntu.com/community/Rsyncmirror)

If you'd like more control over what gets mirrored (more likely), look at something like Debmirror.

[https://help.ubuntu.com/community/Debmirror](https://help.ubuntu.com/community/Debmirror)

You'll want to make the files you've mirrored available to the local systems by http, so you'll need apache or lighttpd running to support that.  Then point the apt repos on the local systems to the local mirror to pick up their updates.

You may be in for more than you bargained for here -- typically local mirrors are only warranted when you've got 50+ systems to care for.

---

### Post by Jussi Kukkonen on 2008-04-07
> **jcostom said:**
> You may be in for more than you bargained for here -- typically local mirrors are only warranted when you've got 50+ systems to care for.

Hmmm? That may be true for full mirroring, but that's not necessary here, AFAICT.

I'd suggest using apt-proxy: [https://help.ubuntu.com/community/AptProxy](https://help.ubuntu.com/community/AptProxy)
It'll only download the stuff you need, and then proxy it for other machines.

---

### Post by shane2peru on 2008-04-07
> **Jussi Kukkonen said:**
> Hmmm? That may be true for full mirroring, but that's not necessary here, AFAICT.

I'd suggest using apt-proxy: [https://help.ubuntu.com/community/AptProxy](https://help.ubuntu.com/community/AptProxy)
It'll only download the stuff you need, and then proxy it for other machines.

Yes Yes Yes!  This looks exactly like what I want!  Wow, doesn't even really have to do with a server installation. lol, that is alright, I want to play with the server install and learn how to do all this anyway.  Thanks for that info!  Excellent!

Shane

---

