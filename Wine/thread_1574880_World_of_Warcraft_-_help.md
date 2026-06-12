---
title: "World of Warcraft - help"
date: 2010-09-14
forum: Wine
---

### Post by Kareta on 2010-09-14
I recently installed World of Warcraft using wine, but I'm having a problem.

When I drag a skill on my UI and I logout or disconnect the next time I log in it isn't there.

I'm playing on a private server, by the way.

Help?

---

### Post by cwwilson721 on 2010-09-14
Could be many reasons

[LIST]
[*]Are you running Compiz? (Big no-no)
[*]Are you running in opengl? (Big yes-yes)
[*]Private server not running correctly (Not saving your stuff)
[/LIST]
The first two would more be about graphics, but those issues can manifest themselves in many other, non-intuitive ways. 

However, I'd lean towards the third possibility. Private servers are NOT running the same code as wow servers. Close, but still far enough to cause many issues.

Do you ever run regular wow servers? Or other private servers? And, if so, do you have the same issue?

---

### Post by Kareta on 2010-09-14
> **cwwilson721 said:**
> Could be many reasons

[LIST]
[*]Are you running Compiz? (Big no-no)
[*]Are you running in opengl? (Big yes-yes)
[*]Private server not running correctly (Not saving your stuff)
[/LIST]
The first two would more be about graphics, but those issues can manifest themselves in many other, non-intuitive ways. 

However, I'd lean towards the third possibility. Private servers are NOT running the same code as wow servers. Close, but still far enough to cause many issues.

Do you ever run regular wow servers? Or other private servers? And, if so, do you have the same issue?

No, not running Compiz.

No, not running in opengl (what is that anyway?)

Private server's don't run the same code as retail servers do, but I've played multiple servers (However I've only played on one so far using wine/WoW).  
No, I don't run retail. 

Perhaps it is the server, I'm not sure if skill UI/setup is cached locally, I thought it was server-side. 

I know macros are cached, dunno about UI setup.

---

### Post by cwwilson721 on 2010-09-14
It's both client and server side..Gets real confusing sometimes...lol

To run in opengl , either add the appropriate line in ~/World of Warcraft/wtf/config.wtf, or add 'opengl' at the end of your launcher command. (Search this forum for examples..TONS in here)

opengl is the open-source community 'attempt' to have a standard like Microsoft's DirectX. DirectX is closed source, and still is not implemented well enough in wine to really use in WoW.  Using opengl really helps your FPS in WoW. (Thus my increase. Look at my sig)

The only time this won't make a difference in gameplay in WoW/wine is if you have a Intel chip. If you do, you're (at least for the foreseeable future) doomed. opengl is NOT correctly implemented in Intel video at the current time. Due to this 'oversight' by Intel, you basically cannot play WoW/wine with a Intel video chip (Or, if you do, it will be so slow and so 'horrible' you would not want to. Play in Windows if you have a Intel chip)

---

### Post by Kareta on 2010-09-14
> **cwwilson721 said:**
> It's both client and server side..Gets real confusing sometimes...lol

To run in opengl , either add the appropriate line in ~/World of Warcraft/wtf/config.wtf, or add 'opengl' at the end of your launcher command. (Search this forum for examples..TONS in here)

opengl is the open-source community 'attempt' to have a standard like Microsoft's DirectX. DirectX is closed source, and still is not implemented well enough in wine to really use in WoW.  Using opengl really helps your FPS in WoW. (Thus my increase. Look at my sig)

The only time this won't make a difference in gameplay in WoW/wine is if you have a Intel chip. If you do, you're (at least for the foreseeable future) doomed. opengl is NOT correctly implemented in Intel video at the current time. Due to this 'oversight' by Intel, you basically cannot play WoW/wine with a Intel video chip (Or, if you do, it will be so slow and so 'horrible' you would not want to. Play in Windows if you have a Intel chip)

No, I don't have an intel chip.

Even after adding opengl in my config.wtf folder it won't cache my UI. (since adding -opengl at the end of my launcher/.exe would be *way* to easy.)

---

### Post by Kareta on 2010-09-14
I just confirmed it being server-side.

I went to another WoW private server, which I know worked on my past Windows PCs, and it worked fine. Even dragged a new skill on the UI and restarted the game, it was still there (Along with what I had on my UI from the last time I had logged onto that server).

Thanks for your help anyway, especially with explaining opengl.

---

### Post by cwwilson721 on 2010-09-15
> **Kareta said:**
> No, I don't have an intel chip.

Even after adding opengl in my config.wtf folder it won't cache my UI. (since adding -opengl at the end of my launcher/.exe would be *way* to easy.)I didn't think it would, but it doesn't hurt.

I also add '-opengl' at the end of my launch command, because I also play in Win7. This way, I don't have to constantly edit the wtf file run in wine every time I copy the win7 install over (I'm amazed at how often I do this. Mostly, every patch..Just easier sometimes...)

Good to see you found what the issue was. Just goes to show you...

Ya never knows whats really going on on them dangburn newfangled computators people are using nowadays....

---

### Post by stephlar on 2010-09-15
> **cwwilson721 said:**
> The only time this won't make a difference in gameplay in WoW/wine is if you have a Intel chip. If you do, you're (at least for the foreseeable future) doomed. opengl is NOT correctly implemented in Intel video at the current time. Due to this 'oversight' by Intel, you basically cannot play WoW/wine with a Intel video chip (Or, if you do, it will be so slow and so 'horrible' you would not want to. Play in Windows if you have a Intel chip)

Do you have any news as to if or when Intel will adopt OpenGL support for their chips?  Or if the open source community has been able to make Intel chips work using OpenGL (such as writing a firmware or driver update - besides xorg)?

---

### Post by cwwilson721 on 2010-09-15
I'd hang up on Intel, for the foreseeable future, at least with WoW/wine. Even the new CPUs with the integrated video are the same video "chipset" as the ones they currently have on the market.

It's not so much the drivers, but the chip itself that's the issue. opengl is not implemented in hardware correctly, so the driver can only do so much.

---

### Post by Rody on 2010-09-16
It actually sounds like you have a permissions problem. I would give the user <what ever you log in as> write permission to all files in the world of warcraft directory.

I had this happen a long time ago when I had dragged my install of WOW from a windows partition, I had to give myself permission to write to files in that directory.

---

### Post by cwwilson721 on 2010-09-16
> **Kareta said:**
> I just confirmed it being server-side.

I went to another WoW private server, which I know worked on my past Windows PCs, and it worked fine. Even dragged a new skill on the UI and restarted the game, it was still there (Along with what I had on my UI from the last time I had logged onto that server).

Thanks for your help anyway, especially with explaining opengl.> **Rody said:**
> It actually sounds like you have a permissions  problem. I would give the user <what ever you log in as> write  permission to all files in the world of warcraft directory.

I had this happen a long time ago when I had dragged my install of WOW  from a windows partition, I had to give myself permission to write to  files in that directory.I guess some people DON'T READ

---

### Post by Jazzy_Jeff on 2010-09-16
> **cwwilson721 said:**
> I guess some people DON'T READ

I guess people could mark THREAD SOLVED!!!

---

