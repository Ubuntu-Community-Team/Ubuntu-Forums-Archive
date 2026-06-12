---
title: "Missing ubuntu"
date: 2005-12-28
forum: The Cafe
---

### Post by Sp@z on 2005-12-28
Wow after issues I had for the last few days and finally getting all my drive space back, I am so totally missing ubuntu/linux. I wasn't that proficent in Linux, but I was learning and I even got my games to run better in Linux than windows! I only play the Ut series so it was pretty easy, but I am back at Windows now, and totally depressed about it. I am also TERRIFIED of screwing up something so bad in LInux I can't bring myself back to reinstalling it. Plus I got the G15 gaming keyboard and Razer Copperhead mouse for Christmas and although they work as basic devices I really wanted them to work in LInux to thier full potential. I know some -ppl are working on a driver for the Keyboard, but have heard NOTHING about the mouse. Maybe I will get my courage back and reinstall Ubuntu soon. I want to say thanx to the community for helping me get my issues corrected and for now I am living up to my promise of staying away from Linux. :(

---

### Post by Aithnea on 2005-12-28
I know how you feel.  I'm still learning everything I can about my computer, which is a laptop.  Ever since I have heard about linux I've been wanting to give it a try but have been totally terrified that I might mess up so badly that I'd kill my computer.  I'm also a web designer so I rely on my computer quite heavily.  I feel terrible using Windows.  Earlier this week though I decided to take the leap and try to see if I can do a dual boot.  Still waiting on getting the Ubuntu CD but I'm totally excited about it.

---

### Post by Sp@z on 2005-12-28
just donwload the live cd. I actually had to download it to fix my computer and it worked like a charm, get used to it then install it when your disks come in the mail.

---

### Post by Lord Illidan on 2005-12-28
[quote=Aithnea]I know how you feel.  I'm still learning everything I can about my computer, which is a laptop.  Ever since I have heard about linux I've been wanting to give it a try but have been totally terrified that I might mess up so badly that I'd kill my computer.  I'm also a web designer so I rely on my computer quite heavily.  I feel terrible using Windows.  Earlier this week though I decided to take the leap and try to see if I can do a dual boot.  Still waiting on getting the Ubuntu CD but I'm totally excited about it.[/quote]

Hehe, I still get this totally excited feeling when installing a Linux distro, hell, even when I boot up... I love it, I live for it, in fact. Er, speaking of web design, can you use nvu?

---

### Post by DevilsAdvocate on 2005-12-28
I suggest dual-booting.  Grab a copy of Partition Magic and resize your Windows drive (unless you have a second drive).  Install Ubuntu on that drive (just make sure to install it to the correct partition).  Your MBR will get over written but GRUB picks windows up no problem.  It's also ridiculously simple to reinstall the Windows bootloader if you want.

---

### Post by Sp@z on 2005-12-29
Yes dual booting is what I did before and due to user ignorance I hosed windows up VERY BAD. I am tetering on the fence of reinstalling again dual boot style.It was the windows MBR that whacked everything up.

---

### Post by anil_robo on 2005-12-29
There have been many threads in the forums when people remove Ubuntu from their hard disks, but then start missing it, only to reinstall it despite whatever problems they have - and most of them do find solutions. Ubuntu, like any other linux, stimulates learning by trying - and indeed I have learnt many things in the last four months with Ubuntu.

I'm not a programmer, but I can now boast of having "compiled" some applications from the "source code" using "gcc"! Which is pretty cool in my opinion, and sometimes I still don't believe I was able to "compile" something - my brother is a software engineer, and he used to tease me that I can't "compile". Now I've sent him an email that I'm able to compile too! :)

Ubuntu is dry without these forums, and I can see how active people are in the forums. I admit, with no regrets, that I have ignored food and phone at times just because I was too busy trying to type a how-to for a newbie. It is this strong community support that one will never get with any other operating system, and it's one of the greatest factors I like about Ubuntu. Most of my problems have been solved in the forums within minutes, and the rest I was able to search - someone solved it much earlier and was kind enough to post the solution.

In fact, my liking for Ubuntu has reached addictive levels, and I recently discovered that I'm not the only one who has fallen in love with Ubuntu - there are  many more just like me! If you see the polls in my signatures, you'll know!

Hardly matters which OS/distro one uses, as long as one practices humanity towards others - that's Ubuntu! :)

---

### Post by poofyhairguy on 2005-12-29
[QUOTE=anil_robo]
I'm not a programmer, but I can now boast of having "compiled" some applications from the "source code" using "gcc"! Which is pretty cool in my opinion, and sometimes I still don't believe I was able to "compile" something - my brother is a software engineer, and he used to tease me that I can't "compile". Now I've sent him an email that I'm able to compile too! :)
[/QUOTE]

Now THAT sounds like an ideal Linux user to me! Not just someone who wants a better Windows, but someone who loves the idea of doing geeky stuff for the sake of it.

With an attitude like that....man...the sky is the limit.

---

### Post by DevilsAdvocate on 2005-12-29
[QUOTE=Sp@z]Yes dual booting is what I did before and due to user ignorance I hosed windows up VERY BAD. I am tetering on the fence of reinstalling again dual boot style.It was the windows MBR that whacked everything up.[/QUOTE]

The key is to install Windows 1st, then install Ubuntu.  That way GRUB gets installed last.  The Windows boot loader doesn't recognize Ubuntu and can cause some grief if done in the other order.  BTW, I've heard it's possible to set XPs boot loader to boot multiple OSs w/ some hacking.  I don't know in fact since I've never tried it.

---

### Post by xmastree on 2006-02-11
[QUOTE=poofyhairguy]someone who loves the idea of doing geeky stuff for the sake of it.[/QUOTE]

I remember ages ago, Mandrake 8.0, I got my soundcard working and discovered that I could play MP3s from a console. No fancy graphical interface, not even a desktop, just a plain old console.

**play /path/to/filename.mp3**

was all it needed. :cool:

That **really** appealed to me... \\:D/

---

### Post by Lord Illidan on 2006-02-11
Doesn't it feel cool to play mp3s from a terminal?? Especially without X...
I love it!

---

### Post by xmastree on 2006-02-11
Have you tried playing videos in a terminal? It's possible.
I can't remember how, but you use mplayer and direct the output somehow.
It's here in the forums... somewhere.

---

### Post by Lord Illidan on 2006-02-11
[quote=xmastree]Have you tried playing videos in a terminal? It's possible.
I can't remember how, but you use mplayer and direct the output somehow.
It's here in the forums... somewhere.[/quote]

I wonder how pr0n would look like... will check.. ;)

---

### Post by BoyOfDestiny on 2006-02-11
It's aalib for blackwhite or libcaca for color ascii. Make sure you've gotten the libraries with apt-get, then try
mplayer -vo aa filename
mplayer -vo caca filename

(Anyway I'm currently on dapper 64... not sure if breezy is compiled with support for these...)

Here are some freaky looking screencaps:

One Piece ep 256.

[[IMG]http://img51.imageshack.us/img51/3791/screenshotmplayer1ca.th.png[/IMG]](http://img51.imageshack.us/my.php?image=screenshotmplayer1ca.png)

Here is one from Bleach 67, a little bigger this time

[[IMG]http://img149.imageshack.us/img149/5889/screenshotmplayer10hp.th.png[/IMG]](http://img149.imageshack.us/my.php?image=screenshotmplayer10hp.png)

Also, if you want a cool text demo made with aalib (has music!), try apt-get install bb

Gotta say, it's fun to play with this stuff if X breaks or you don't have an x server running. :)

---

### Post by xmastree on 2006-02-11
bb, eh? Hmm...

I d/l and installed it, ran it, answered yes, it filled the screen with letters, faster and faster.
I thinks "**this is gonna be so cool...**"
then it stopped. Just music?

Bit of an anticlimax... what's supposed to happen?

---

### Post by BoyOfDestiny on 2006-02-11
Aww... again it works in dapper... Well it's like an old school intro, with text, effects like zooming, 3d rotation, mandelbrot, etc all using ascii. Has photos of some of the coders, with dossiers... Just kind of cool thing that shows off aalib... I guess you can always try getting it backported... =)

---

### Post by xmastree on 2006-02-11
If I turn off the sound, the graphic demo works. But with the sound on it stops just as the sound starts up. :-(

I remember the old school intros, downloading them from a BBS via a 1200 baud modem. They were cool. :cool:

---

