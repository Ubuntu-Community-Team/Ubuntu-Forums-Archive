---
title: "Frustrated with screencasting"
date: 2009-04-12
forum: Ubuntu Studio
---

### Post by wd5gnr on 2009-04-12
I have often made screencasts in both Windows and Linux. However, lately I've been pulling my hair out -- especially since I am taking a class that (foolishly, in my opinion) makes us do screencasts of our work.

I suspect the problem is that I run 64 bit Kubuntu (8.10, all up to date). I have tried:

xvidcap
Istanbul
recordmyscreen
wink
ScreenCastle (web)
Screentoaster (web)
Screncastomatic (web)

Most of these work to some extent but have random issues. Instanbul crashes if you want to record sound. Recordmyscreen records the sound either sped up, backwards or both (hard to tell). The Web ones work with varying degrees of usefulness.

So I usually wind up with an ogv file from record my screen. Then I get to part 2 of my hassle: Video editing.

I really LIKE Cinelerra's feature set (UI is iffy, but the features are good). But it crashes frequently. Worse, half the time I can't get it to render whatever I am looking at, so you do 2 hours of work getting your pan and zoom and then you can't export it. Hard crash. Kdenlive seems to work better -- not as many features and the occasional crash (which it does recover from which is nice). Lives, Open Movie Editor, and pitivi don't really do it for me either. 

So Cinelerra usually won't read the whole ogv file. So then you have to convert it. But the converters don't always work. Or if they do, Cinelerra may only get the sound even though the players can find video and audio. Most of the others won't read the ogv at all so either way you have to convert. ffmpeg seems to work ok. VLC can never find output codecs that it wants to convert which is a shame since that's an easy way to do it.

So yeah I'm whining at this point. But the question is: does anyone have a reasonable tool set to do screen casting on 64-bit? Does everyone fight it like I do? I do get it work eventually (search wd5gnr on YouTube if you like) but it is always a protracted affair. I'd do many more of them if it weren't constant crashing and conversions and frustrations. Or is it just the state of 64-bit?

I'm actually considering using my XP Virtual Box session to do Video editing. That would be really offensive.

---

### Post by wd5gnr on 2009-04-15
Well I guess no one shares my frustration ;-)

Here's the awful truth. I have reverted to using XP in a VirtualBox. On XP I run XMing (could have used Cygwin) and run my app on the VirtualBox screen (from a shell prompt: DISPLAY=virtualxp:0 theapp) and then use a copy of Camtasia (whatever its called -- from TechSmith) to do the capture under Windows. Ugh. Then I do the live capture on a Vista laptop (double ugh) that I normally boot Kubuntu on but left it dual boot for just such cases. Can't seem to get VirtualBox to let the USB Web cam show through to XP.

This is the first "basic task" I've had in a long time that I could not solve reasonably under Linux unless you count problems running specific software packages (e.g., Dazzle internet postage still doesn't work well under Wine). But there seems to be no adequate tool for creating and editing video content on 64 bit, at least.

It is a shame about Cinelerra. It does it all. But it crashes so much there is a menu option to recover from the crash (learned about that). And it simply won't render. The only render that did anything was the QT4L output and it produced video that had the wrong color palette (looked like an acid trip, er-if I knew what an acid trip looked like). Kdenlive is simple and easy to use but also crash prone. In addition, separating the audio introduced horrible lip sync issues. And despite having things lined up on the time line (like text titles, a graphic,  and music) they would not line up in the rendered output. Oh, and the transitions don't seem to work well although that could be operator error since I just gave up on them and didn't try hard.

So before I thought about VirtualBox I did use Kdenlive to splice a title on the front and back of a video captured under XP and a screecap from recordmyscreen. I recorded audio with Audacity (which works great) and put that under the screen capture. Then the output from Kdenlve had big black gaps where it switched tracks (shouldn't have been there) so I poured the video through avidemux and used it to chop the black spots out (mostly). The result was pretty poor compared to what I had envisioned. The audio does not fade, the video segments don't transition, and I look old and tired (well, that last part isn't the software's fault).

Here's the result of that: [http://www.youtube.com/watch?v=12iAP7MY1xE](http://www.youtube.com/watch?v=12iAP7MY1xE)

If I redo it, it will be with the virtual box solution which works great. What a shame.

Just thought I'd share the result with anyone else struggling to do the same thing. Maybe one day I'll get some time and try my hand at writing a better editor or at least debug and fix cinelerra. But that won't be today.

P.S. I had tried LIVES but it wouldn't even start. Figured out why. It really wants to load jackd for audio. However, if anything might be using Alsa (e.g., Firefox) jackd won't load and Lives just kind of quits. So you either have to reset Alsa (which closes everything thinking about using sound) or recompile LIVES without Jackd support (which cripples it). Haven't tried it to see if it works any better than the rest, but it is another option which I didn't try because I couldn't get it to start.

---

