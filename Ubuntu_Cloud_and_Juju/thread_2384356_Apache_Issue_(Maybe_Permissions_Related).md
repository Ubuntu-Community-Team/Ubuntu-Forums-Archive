---
title: "Apache Issue (Maybe Permissions Related)"
date: 2018-02-06
forum: Ubuntu Cloud and Juju
---

### Post by TheMTtakeover on 2018-02-06
I am having a bit of an issue when using using the html5 audio player to point at a file to play. It will only play files that have been placed in the Document Root folder (/var/www/html/) at one point.

For example:

I have two files in the same folder one named throw_it_up.mp3 and one named throw_it_upp.mp3. The output of ls -la

[code
]-rwxr-x---. 1 themttakeover apache  3092792 Feb  6 09:35 throw_it_up.mp3
-rwxr-x---. 1 themttakeover apache  3092792 Feb  5 22:05 throw_it_upp.mp3
[/code]

The permissions on these files appear to be exactly the same, but I can only set the html5 player to play the one with a single p in "up". The only difference between the two files is that one was placed in the /var/www/html/ folder and then moved to it's current location where as the other was not placed in /var/www/html/ before being moved to it's current location. They are both located at /var/www/html/teamtaji/mt1/. They are the same file with one having a different name.

I obviously do not want to have to place all of my files in the Document Root folder and then move them to where they need to go, it would save a lot of time if I can figure out what is happening to the files when they are placed into the Document Root folder that is not occurring otherwise.


EDIT: It is a permissions issue but I still do not know how to resolve it. Here is a sample of my error logs file:

```
[Mon Feb 05 22:14:14.265391 2018] [core:error] [pid 14850] (13)Permission denied: [client 73.175.48.26:35716] AH00132: file permissions deny server access: /var/www/html/teamtaji/mt1/01imon.mp3, referer: [http://pinkislandturtle.com/teamtaji/mt1.html](http://pinkislandturtle.com/teamtaji/mt1.html)
[Mon Feb 05 22:16:44.861984 2018] [core:error] [pid 14848] (13)Permission denied: [client 73.175.48.26:47083] AH00132: file permissions deny server access: /var/www/html/teamtaji/mt1/01imon.mp3, referer: [http://pinkislandturtle.com/teamtaji/mt1.html](http://pinkislandturtle.com/teamtaji/mt1.html)
[Tue Feb 06 05:56:30.327744 2018] [core:error] [pid 15078] (13)Permission denied: [client 72.21.196.64:25204] AH00132: file permissions deny server access: /var/www/html/teamtaji/mt1/01imon.mp3, referer: [http://www.pinkislandturtle.com/teamtaji/mt1/](http://www.pinkislandturtle.com/teamtaji/mt1/)
[Tue Feb 06 08:49:58.731036 2018] [core:error] [pid 14850] (13)Permission denied: [client 73.175.48.26:45620] AH00132: file permissions deny server access: /var/www/html/teamtaji/mt1/01imon.mp3, referer: [http://pinkislandturtle.com/teamtaji/mt1/mt1.html](http://pinkislandturtle.com/teamtaji/mt1/mt1.html)
[Tue Feb 06 08:51:01.424834 2018] [core:error] [pid 14849] (13)Permission denied: [client 73.175.48.26:39260] AH00132: file permissions deny server access: /var/www/html/teamtaji/mt1/imon.mp3, referer: [http://pinkislandturtle.com/teamtaji/mt1/mt1.html](http://pinkislandturtle.com/teamtaji/mt1/mt1.html)
[Tue Feb 06 08:52:04.546028 2018] [core:error] [pid 17144] (13)Permission denied: [client 73.175.48.26:33922] AH00132: file permissions deny server access: /var/www/html/teamtaji/mt1/imon.mp3, referer: [http://pinkislandturtle.com/teamtaji/mt1/mt1.html](http://pinkislandturtle.com/teamtaji/mt1/mt1.html)
[Tue Feb 06 08:54:46.290083 2018] [core:error] [pid 14851] (13)Permission denied: [client 73.175.48.26:37148] AH00132: file permissions deny server access: /var/www/html/teamtaji/mt1/imon.mp3, referer: [http://pinkislandturtle.com/teamtaji/mt1/mt1.html](http://pinkislandturtle.com/teamtaji/mt1/mt1.html)
[Tue Feb 06 08:56:17.869371 2018] [core:error] [pid 14850] (13)Permission denied: [client 73.175.48.26:48494] AH00132: file permissions deny server access: /var/www/html/teamtaji/mt1/imon.mp3, referer: [http://pinkislandturtle.com/teamtaji/mt1/mt1.html](http://pinkislandturtle.com/teamtaji/mt1/mt1.html)
[Tue Feb 06 09:20:03.876573 2018] [core:error] [pid 15078] (13)Permission denied: [client 73.175.48.26:34502] AH00132: file permissions deny server access: /var/www/html/teamtaji/mt1/meal_ticket.zip, referer: [http://pinkislandturtle.com/teamtaji/mt1/mt1.html](http://pinkislandturtle.com/teamtaji/mt1/mt1.html)
[Tue Feb 06 09:22:23.933580 2018] [core:error] [pid 17146] (13)Permission denied: [client 73.175.48.26:38961] AH00132: file permissions deny server access: /var/www/html/teamtaji/mt1/meal_ticket.zip, referer: [http://pinkislandturtle.com/teamtaji/mt1/mt1.html](http://pinkislandturtle.com/teamtaji/mt1/mt1.html)
[Tue Feb 06 09:23:18.614831 2018] [core:error] [pid 14851] (13)Permission denied: [client 73.175.48.26:45101] AH00132: file permissions deny server access: /var/www/html/teamtaji/mt1/meal_ticket.zip, referer: [http://pinkislandturtle.com/teamtaji/mt1/mt1.html](http://pinkislandturtle.com/teamtaji/mt1/mt1.html)
[Tue Feb 06 09:27:44.404100 2018] [core:error] [pid 17145] (13)Permission denied: [client 73.175.48.26:35008] AH00132: file permissions deny server access: /var/www/html/teamtaji/mt1/meal_ticket.zip, referer: [http://pinkislandturtle.com/teamtaji/mt1/mt1.html](http://pinkislandturtle.com/teamtaji/mt1/mt1.html)
[Tue Feb 06 09:33:16.843972 2018] [core:error] [pid 15078] (13)Permission denied: [client 73.175.48.26:38675] AH00132: file permissions deny server access: /var/www/html/teamtaji/mt1/throw_it_up.mp3, referer: [http://pinkislandturtle.com/teamtaji/mt1/mt1.html](http://pinkislandturtle.com/teamtaji/mt1/mt1.html)
[Tue Feb 06 09:34:16.680932 2018] [core:error] [pid 17146] (13)Permission denied: [client 73.175.48.26:48220] AH00132: file permissions deny server access: /var/www/html/teamtaji/mt1/throw_it_up.mp3, referer: [http://pinkislandturtle.com/teamtaji/mt1/mt1.html](http://pinkislandturtle.com/teamtaji/mt1/mt1.html)
[Tue Feb 06 09:40:02.187718 2018] [core:error] [pid 14848] (13)Permission denied: [client 73.175.48.26:33722] AH00132: file permissions deny server access: /var/www/html/teamtaji/mt1/throw_it_up.mp3.old, referer: [http://pinkislandturtle.com/teamtaji/mt1/mt1.html](http://pinkislandturtle.com/teamtaji/mt1/mt1.html)
[Tue Feb 06 09:41:17.513726 2018] [core:error] [pid 17143] (13)Permission denied: [client 73.175.48.26:43895] AH00132: file permissions deny server access: /var/www/html/teamtaji/mt1/throw_it_up.mp3.old, referer: [http://pinkislandturtle.com/teamtaji/mt1/mt1.html](http://pinkislandturtle.com/teamtaji/mt1/mt1.html)
[Tue Feb 06 09:44:30.252143 2018] [core:error] [pid 15078] (13)Permission denied: [client 73.175.48.26:33409] AH00132: file permissions deny server access: /var/www/html/teamtaji/mt1/throw_it_upp.mp3, referer: [http://pinkislandturtle.com/teamtaji/mt1/mt1.html](http://pinkislandturtle.com/teamtaji/mt1/mt1.html)
[Tue Feb 06 09:48:03.171794 2018] [core:error] [pid 17146] (13)Permission denied: [client 73.175.48.26:32833] AH00132: file permissions deny server access: /var/www/html/teamtaji/mt1/throw_it_upp.mp3, referer: [http://pinkislandturtle.com/teamtaji/mt1/mt1.html ]("http://pinkislandturtle.com/teamtaji/mt1/mt1.html")
```

---

### Post by TheMTtakeover on 2018-02-06
Marking as resolved

---

