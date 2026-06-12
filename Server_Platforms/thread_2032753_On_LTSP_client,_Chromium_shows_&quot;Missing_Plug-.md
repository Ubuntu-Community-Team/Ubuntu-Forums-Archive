---
title: "On LTSP client, Chromium shows &quot;Missing Plug-in&quot; at YouTube"
date: 2012-07-24
forum: Server Platforms
---

### Post by JD Hupp on 2012-07-24
[SIZE=-1][FONT=Arial]Still learning, probing,           troubleshooting on a modest 2-PC server-client setup:
          
          A Lubuntu 12.04 + LTSP 5 server with AMD Athlon 1300 and 512MB plays YouTube videos           in Chromium 18 well enough (at least if you don't set it to           full-screen).
          
          But LTSP clients (Client #1: Celeron 466, 192MB --- then swapped in Client #2: PIII 733, 256MB) just show           the play window blank except for a **Missing Plug-in**           message.
          
          Anyone know why this isn't working or how I can make it work?
          
          --John Hupp[/FONT][/SIZE]

---

### Post by JD Hupp on 2012-07-26
[SIZE=-1][FONT=Arial]More experimentation: 

        [/FONT][/SIZE][SIZE=-1][FONT=Arial]I booted           the Lubuntu 12.04 i386 desktop Live CD standalone on the PIII           733MHz, 256MB machine.  As one might expect on that hardware,           YouTube performance was miserable, but Chromium did not give           me a blank play window with **Missing Plug-in**, it did           play a video.
          
          So this does seem to be an LTSP question.[/FONT][/SIZE]

[SIZE=-1][FONT=Arial]         I then set up an Edubuntu 12.04 LTSP server with a Celeron 2.8 GHz         and 512MB and installed Chromium.  Then I connected the same         PIII 733Mhz, 256MB machine as a terminal.  YouTube videos played         fine, with no **Missing Plug-in** failure message.
        
        So the only difference that I can see, other than Celeron 2.8         GHz vs. Athlon 1300 on the server, is that the failure case         involved Lubuntu LTSP instead of Ubuntu LTSP.  Which is to say,         it seems that the issue is related to the LTSP implementation on         Lubuntu.
        
        Is that a helpful clue to anyone?
        
        (By the way, I checked to see that Chromium was not playing the video via YouTube's HTML5 trial.  It was using Flash.)
        
[/FONT][/SIZE]

---

