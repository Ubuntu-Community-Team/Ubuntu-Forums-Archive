---
title: "Xvid is an unsupported format; kdenlive won't let me select it for rendering"
date: 2009-05-12
forum: Ubuntu Studio
---

### Post by diablo75 on 2009-05-12
I'm not sure what to make of this problem, as it doesn't seem to exist on my laptop.  But on my PC, when I go to render a project in kdenlive, very few video codecs are selectable.  I'd like to be able to render into an xvid, but not sure how to get it working.  Anyone know?

---

### Post by diablo75 on 2009-05-12
I'm not sure what did it, but I got it to work.

Here's what I did.

I have had the Ubuntu Restricted Extra's installed on here, but not the Kubuntu Restricted.  So I installed those.  That alone didn't fix it.  I then went into kdenlive, and clicked Settings>Run Config Wizard.  This went through and apparently re-detected all available video and audio codecs, and I just had to click Next>Next>Next.  Once done, I was able to select between all listed video codecs, including xvid.

---

### Post by colas on 2009-06-15
Actually, you do not need to install the whole kubuntu restricted (which may trigger conflicts), just installing 

[LIST]
[*]libavcodec-unstripped-52
[*]libavformat-unstripped-52
[/LIST]
and re -running through the "Settings>Run Config Wizard" should be ok.

---

### Post by ttguy on 2011-10-15
Under Natty the installation of libavcodec-extra-52 would appear to fix this issue  - if you re-run the config wizard afterwards and quit out of any other instances you have of kdenlive that might be running as a different user.

---

