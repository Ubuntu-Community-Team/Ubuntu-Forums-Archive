---
title: "Kindle"
date: 2010-08-15
forum: Wine
---

### Post by Tiiba on 2010-08-15
I used to use Kindle for PC on Linux. Today, I had a problem that forced me to reinstall Ubuntu. Then I updated everything and downloaded a bunch of other programs, including Wine and the Kindle installer. I installed it and ran the program. It died without messages. I configured Wine to emulate Win98 and tried again. No help. I downgraded Wine to 1.0. No help. I reinstalled Kindle. No help. I launched it from the terminal, to see if there's a missing DLL. It didn't tell me.

And so I come here. WTF?

[PHP]env WINEPREFIX="/home/user/.wine" wine "C:\\Program Files\\Amazon\\Kindle For PC\\KindleForPC.exe" 
err:menubuilder:WinMain unknown option -a
err:menubuilder:WinMain unknown option -r
err:alsa:ALSA_CheckSetVolume Could not find 'PCM Playback Volume' element
fixme:mixer:ALSA_MixerInit No master control found on USB Device 0x46d:0x802, disabling mixer
fixme:mixer:ALSA_MixerInit No master control found on USB Device 0xd8c:0x0c, disabling mixer
fixme:system:SystemParametersInfoW Unimplemented action: 8202 (SPI_GETFONTSMOOTHINGTYPE)
fixme:system:SetProcessDPIAware stub!
fixme:system:SystemParametersInfoW Unimplemented action: 8204 (SPI_GETFONTSMOOTHINGCONTRAST)
err:ole:CoGetClassObject class {6e4fcb12-510a-4d40-9304-1da10ae9147c} not registered
err:ole:CoGetClassObject class {6e4fcb12-510a-4d40-9304-1da10ae9147c} not registered
err:ole:create_server class {6e4fcb12-510a-4d40-9304-1da10ae9147c} not registered
fixme:ole:CoGetClassObject CLSCTX_REMOTE_SERVER not supported
err:ole:CoGetClassObject no class object {6e4fcb12-510a-4d40-9304-1da10ae9147c} could be created for context 0x17
fixme:crypt:CertGetNameStringW unimplemented for type 2[/PHP]

---

### Post by cogadh on 2010-08-15
You might need to install a native DCOM. Easiest way to do that is with [winetricks]("http://wiki.winehq.org/winetricks").

---

### Post by hikaricore on 2010-08-15
It should be worth mentioning that unlike windows, very few problems should ever force you to reinstall Ubuntu...

---

### Post by ElNerdoDeGeek on 2010-08-17
I'm experiencing what appears to be the same problem. If anybody knows how to get Kindle for PC running in Linux again, please let me know. =(

---

### Post by kub-fu on 2010-08-26
Following cogadh advice I installed DCOM98 and setup the overrides for comcat.dll and olethk32.dll to use the native libraries. That got rid of most of the errors but this one:

fixme:system:SetProcessDPIAware stub!

That doesn't seem like a fatal error, but the app never opens.

---

### Post by mlevin77 on 2010-09-26
> **kub-fu said:**
> Following cogadh advice I installed DCOM98 and setup the overrides for comcat.dll and olethk32.dll to use the native libraries. That got rid of most of the errors but this one:

fixme:system:SetProcessDPIAware stub!

That doesn't seem like a fatal error, but the app never opens.

  I've got the same problem. Did you ever solve this?

Mike

---

### Post by kub-fu on 2010-09-26
Nope, I settled on using the old version.

---

### Post by mlevin77 on 2010-09-26
> **kub-fu said:**
> Nope, I settled on using the old version.

  sorry, what old version - do you mean there's an older version of the Kindle.exe app that does work?

Mike

---

### Post by kub-fu on 2010-09-26
Yeah, it's the old beta version. If you search for "kindle beta linux" you'll probably find it.

---

### Post by mlevin77 on 2010-09-26
> **kub-fu said:**
> Yeah, it's the old beta version. If you search for "kindle beta linux" you'll probably find it.

   hmmm. I've been googling for a while - all the links point to Amazon which has updated it and always gives the latest version. Surely someone has a link to, or can post to rapidshare or whatever, the working beta?

Mike

---

### Post by ajackson on 2010-09-27
Have a read of [this]("http://ubuntuforums.org/showthread.php?t=1326044") thread, start at the latest and work backwards to find the last known good download site for the beta version. If that link no longer works try posting in that thread to see if someone can repost it for you.

---

### Post by Jazzy_Jeff on 2010-09-27
Here is a link to get the version that works [http://www.blogsdna.com/5575/read-kindle-books-on-your-computer-with-amazon-kindle-for-pc-beta.htm](http://www.blogsdna.com/5575/read-kindle-books-on-your-computer-with-amazon-kindle-for-pc-beta.htm). It is towards the bottom of the post.

---

### Post by regeya on 2011-02-25
If you use the **[B]wine-1.3**[/B] package from the [Wine PPA]("http://www.winehq.org/download/deb"), the version of Kindle for PC on the Amazon website runs just fine.

:guitar:

I figured it had to be something simple; it ran just fine for me on Fedora 14.

---

