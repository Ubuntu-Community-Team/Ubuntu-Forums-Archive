---
title: "Warcraft III run problems"
date: 2009-02-25
forum: Wine
---

### Post by enduser000 on 2009-02-25
Hello,
    I recently installed wine. It worked on kubuntu when I installed it on my other partition, (just gave me a sound error) so I figured I'd instsall it on my main partition (Ubuntu 8.10, still running gnome).
    So I installed wine (sudo aptitude install wine).  That went fine.
    I installed wc3 (using the original cd's/cd keys).
    I then clicked "Play warcraft 3" and it gives me this error: ```
Please verify that your Warcraft III disc is un your CD-ROM drive, then click on 'Retry'.
```
        It then displays:
```
This application has encountered a critical error:

FATAL ERROR!

Program: C:\Program Files\Warcraft III\War3.exe
Exception: 0xC0000005 (ACCESS_VIOLATION) at 0073:00000000

The instruction at '0x00000000' referenced memory at '0x00000000'.
The memory could not be 'read'.

Press OK to terminate the application.

```
      I currently have wine configured to 'Windows XP' and it sees the drive (in config>Drives, D:  /media/Warcraft III) when I have my disc inserted.
      I tried reinstalling and also completely removing (.wine under home) and using aptitude and synaptic to remove wine completely.  I have gotten the same results each time.  I also got an error before (on the first install of wine) that warcraft 3 could not find my cdrom drive, but that's not coming up now.
      Any help is appreciated, I've been through the appdb and other how-to's and posts.  I also renamed the intro movies so it didn't crash.  Let me know what you think I should try next as this is about the only thing I use windows for anymore.

end

---

### Post by enduser000 on 2009-02-26
Tried a few more things...

Completely removed wine and installed latest version (1.1.15)

Installed fusion-icon to switch to metacity while running warcraft

Patched warcraft TFT to version 1.22 to avoid having to use the CD

Tried it with a virtual desktop

I now get the 'FATAL ERROR' right away, and when I hit okay, it says please insert wc3 into your cdrom (though it says patch 1.22 was successful).  When I click retry, it gives me the fatal error again

Any ideas?

enduser

---

### Post by enduser000 on 2009-02-26
[SOLVED]
Had to add myself to the 'video' group as wine was unable to access a nvidia file it needed.

works perfectly now.

gz to arethusa on #winehq for the solution

---

