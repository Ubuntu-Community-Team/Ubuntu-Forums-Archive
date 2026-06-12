---
title: "WoW Launch Error with Wine"
date: 2010-02-27
forum: Wine
---

### Post by Pietervl on 2010-02-27
Hi all,
I am using Ubuntu 9.10 for a while now, and the only thing left where I use Windows for is to play WOW.  I can't get the game working under the Wine emulator, and I really looked it up on all the forums, but havent found the solution (yet) ...

When I want to start up the game (via Wine), a error (#132) message appears, and I cant even see the login screen of the game. I am using Wine version 1.0.1
The link contains a screenshot of the error:
[http://s705.photobucket.com/albums/ww59/Pietervl/?action=view&current=wowerror.png](http://s705.photobucket.com/albums/ww59/Pietervl/?action=view&current=wowerror.png)

Please anyone help, so I can use my Ubuntu machine for everything and so I can finally throw my Windows PC out of the window!

---

### Post by Marvin666 on 2010-02-28
Two other people (myself included) are having this same error in the how to thread.

---

### Post by UnhappyLinux on 2010-03-01
Well, here is my 2 cents hope it helps you.

I Installed Ubuntu, then Wow, it played great.

I then followed advice in another forum and typed in (don't remember now) some command in Terminal and WoW stopped playing in wine.

So I read the forums, kicked myself in the butt for touching something I know nothing about...etc.

Went into WineCfg and told it to "detect" paths/drives..or whatever that was and it showed a few drives. I told it too remove the drive reference to "home" as someone said it someplace on these forums, I just remember him saying to NOT have that there.

Sorry so vague and simple on the descriptions, just remembering the events of that day.

Anyway, after that WoW works with no problems. So to sum it up, winecfg>autodetect>remove ref to `home and try it out.

Best

---

### Post by Soulcage on 2010-03-02
You should try upgrading wine to 1.1.39 then try.

---

### Post by Pietervl on 2010-03-02
I solved the problem, this is the way I did:

1. Update to the latest version of Wine (I am using 1.1.39 at the moment). Just do it via System>Administration>update manager

2. Copy the entire game folder to the c:\ drive from Wine.

3. Run the 'Repair Tool', included in the folder. This tool will also remove all your addons, so copy them first to another location if you need them later!! (this may take a while)

4. Use the 'Launcher.exe' to start the game instead of 'wow.exe'

5. Your WoW should work now! It worked for me, hope it works for you

---

