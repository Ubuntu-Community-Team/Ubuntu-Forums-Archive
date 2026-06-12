---
title: "Internet TV: are those CCTV working for your ?"
date: 2011-01-02
forum: The Cafe
---

### Post by honeybear on 2011-01-02
I found this script to watch TV using bash and linux:
 
```


#!/bin/sh
#Hawkeye34's British TV Shell Script
#Version 1.53 (first release, 53 channels)
#Written on 19 March 2010 for myp2pforum.eu
#Looking for live sport schedules? Visit myp2p.eu | myp2p.us | myp2p.nl
while true; do
   echo -e "British TV for Linux! | Hawkeye34 - myp2pforum.eu | Version 1.53: 19 March 2010"
   #!!DO NOT EDIT AFTER THIS POINT UNLESS YOU KNOW WHAT YOU ARE DOING!!
   echo -e "1. BBC1\t\t\t23. History\t\t\t45. ITV1 (LQ)"
   echo -e "2. BBC2\t\t\t24. Discovery\t\t\t46. ITV2 (LQ)"
   echo -e "3. ITV1\t\t\t25. Movies 1\t\t\t47. ITV3 (LQ)"
   echo -e "4. Channel 4\t\t26. Movies 2\t\t\t48. CBS Reality (LQ)"
   echo -e "5. Five\t\t\t27. Movies 3\t\t\t49. BBC News24 (LQ)"
   echo -e "6. BBC3\t\t\t28. Movies 4\t\t\t50. Bloomberg (LQ)"
   echo -e "7. BBC4\t\t\t29. Eurosport\t\t\t51. Deutsche Welle"
   echo -e "8. ITV2\t\t\t30. BBC News24\t\t\t52. CNN International"
   echo -e "9. ITV3\t\t\t31. Sky News\t\t\t53. CNN Int'l (LQ)"
   echo -e "10. ITV4\t\t32. Sky News Headlines"
   echo -e "11. E4\t\t\t33. BBC Parliament"
   echo -e "12. More4\t\t34. Bloomberg TV"
   echo -e "13. CBS Reality\t\t35. Russia Today"
   echo -e "14. 4Music\t\t36. Scuzz"
   echo -e "15. Zone Horror\t\t37. Flaunt"
   echo -e "16. Film4\t\t38. France 24"
   echo -e "17. Classic Movies2\t39. BBC1 (LQ)"
   echo -e "18. James Bond TV\t40. BBC2 (LQ)"
   echo -e "19. QVC\t\t\t41. BBC3 (LQ)"
   echo -e "20. S4C\t\t\t42. C4 (LQ)"
   echo -e "21. Fashion TV\t\t43. E4 (LQ)"
   echo -e "22. ClassicFM TV\t44. Five (LQ)"
   echo -e "Enter "exit" to quit to console!"
   echo -n "Please enter a channel number: "
   read chnum
   #Begin VLC commands.
   case $chnum in

      "1") echo -e "Starting BBC1...\n"
      mplayer http://cctv.ws/7/BBC1
      ;;
      "2") echo -e "Starting BBC2...\n"
      mplayer http://cctv.ws/7/BBC2
      ;;
      "3") echo -e "Starting ITV1...\n"
      mplayer http://cctv.ws/2/ITV1
      ;;
      "4") echo -e "Starting Channel Four...\n"
      mplayer http://cctv.ws/5/ChannelFour
      ;;
      "5") echo -e "Starting Five...\n"
      mplayer http://cctv.ws/0/s3byz/Five
      ;;
      "6") echo -e "Starting BBC3...\n"
      mplayer http://cctv.ws/9/BBC3
      ;;
      "7") echo -e "Starting BBC4...\n"
      mplayer http://cctv.ws/7/CBeebies/BBC4
      ;;
      "8") echo -e "Starting ITV2...\n"
      mplayer http://cctv.ws/0/NhYpi4/ITV2
      ;;
      "9") echo -e "Starting ITV3...\n"
      mplayer http://cctv.ws/0/ITV3
      ;;
      "10") echo -e "Starting ITV4...\n"
      mplayer http://cctv.ws/3/rrU5j/ITV4
      ;;
      "11") echo -e "Starting E4...\n"
      mplayer http://cctv.ws/5/E4Channel
      ;;
      "12") echo -e "Starting More4...\n"
      mplayer http://cctv.ws/3/More4
      ;;
      "13") echo -e "Starting CBS Reality...\n"
      mplayer http://cctv.ws/6/CBSReality
      ;;
      "14") echo -e "Starting 4Music...\n"
      mplayer http://cctv.ws/3/4Music
      ;;
      "15") echo -e "Starting Zone Horror...\n"
      mplayer http://cctv.ws/1/ZoneHorror
      ;;
      "16") echo -e "Starting Film4...\n"
      mplayer http://cctv.ws/1/3eZ1R1/Film4
      ;;
      "17") echo -e "Starting Classic Movies2...\n"
      mplayer http://cctv.ws/4/classicmovies2
      ;;
      "18") echo -e "Starting James Bond TV...\n"
      mplayer http://cctv.ws/2/JamesBondTV
      ;;
      "19") echo -e "Starting QVC...\n"
      mplayer http://cctv.ws/2/qvcuk
      ;;
      "20") echo -e "Starting S4C...\n"
      mplayer mms://cctv.ws/7/S4Cdigidol
      ;;
      "21") echo -e "Starting Fashion TV...\n"
      mplayer http://cctv.ws/0/FashionTV
      ;;
      "22") echo -e "Starting ClassicFM TV...\n"
      mplayer http://cctv.ws/6/cfmtv
      ;;
      "23") echo -e "Starting History...\n"
      mplayer http://cctv.ws/9/1wbeA4/History
      ;;
      "24") echo -e "Starting Discovery...\n"
      mplayer http://cctv.ws/9/DiscoveryChannel
      ;;
      "25") echo -e "Starting Movies 1...\n"
      mplayer http://cctv.ws/7/somethingmovies1
      ;;
      "26") echo -e "Starting Movies 2...\n"
      mplayer http://cctv.ws/9/somethingmovies2
      ;;
      "27") echo -e "Starting Movies 3...\n"
      mplayer http://cctv.ws/1/somethingmovies3
      ;;
      "28") echo -e "Starting Movies 4...\n"
      mplayer http://cctv.ws/2/ovies3 #Yes, this is the right channel. cctv.ws was having issues.
      ;;
      "29") echo -e "Starting Eurosport...\n"
      mplayer http://cctv.ws/1/BritishEurosport
      ;;
      "30") echo -e "Starting BBC News24...\n"
      mplayer http://cctv.ws/8/BBCNews
      ;;
      "31") echo -e "Starting Sky News...\n"
      mplayer http://cctv.ws/2/SkyNews
      ;;
      "32") echo -e "Starting Sky News Headlines...\n"
      mplayer mms://live1.wm.skynews.servecast.net/skynews_wmlz_live300k
      ;;
      "33") echo -e "Starting BBC Parliament...\n"
      mplayer http://cctv.ws/5/bbcpar
      ;;
      "34") echo -e "Starting Bloomberg TV...\n"
      mplayer http://cctv.ws/6/BloombergUK
      ;;
      "35") echo -e "Starting Russia Today...\n"
      mplayer http://cctv.ws/9/RussiaToday
      ;;
      "36") echo -e "Starting Scuzz...\n"
      mplayer http://cctv.ws/1/Scuzz
      ;;
      "37") echo -e "Starting Flaunt...\n"
      mplayer http://cctv.ws/3/Flaunt
      ;;
      "38") echo -e "Starting France 24...\n"
      mplayer http://cctv.ws/6/France24En
      ;;
      "39") echo -e "Starting BBC1 (LQ)...\n"
      mplayer http://cctv.ws/6/BBC1LQ
      ;;
      "40") echo -e "Starting BBC2 (LQ)...\n"
      mplayer http://cctv.ws/1/BBC2LQ
      ;;
      "41") echo -e "Starting BBC3 (LQ)...\n"
      mplayer http://cctv.ws/5/BBC3lq
      ;;
      "42") echo -e "Starting Channel Four (LQ)...\n"
      mplayer http://cctv.ws/3/C4LQ
      ;;
      "43") echo -e "Starting E4 (LQ)...\n"
      mplayer http://cctv.ws/1/e4lQ
      ;;
      "44") echo -e "Starting Five (LQ)...\n"
      mplayer http://cctv.ws/1/FivelQ
      ;;
      "45") echo -e "Starting ITV1 (LQ)...\n"
      mplayer http://cctv.ws/3/ITV1LQ
      ;;
      "46") echo -e "Starting ITV2 (LQ)...\n"
      mplayer http://cctv.ws/8/TV2lq/ITV2LQ
      ;;
      "47") echo -e "Starting ITV3 (LQ)...\n"
      mplayer http://cctv.ws/4/ITV3LQ
      ;;
      "48") echo -e "Starting CBS Reality (LQ)...\n"
      mplayer http://cctv.ws/4/CBSRealityLQ
      ;;
      "49") echo -e "Starting BBC News24 (LQ)...\n"
      mplayer http://cctv.ws/3/BBCnewsLQ
      ;;
      "50") echo -e "Starting Bloomberg (LQ)...\n"
      mplayer http://cctv.ws/8/BloombergLQ
      ;;
      "51") echo -e "Die Deutsche Welle startet...\n"
      mplayer http://cctv.ws/0/DeutscheWelle
      ;;
      "52") echo -e "Starting CNN International...\n"
      mplayer http://cctv.ws/7/CNNint
      ;;
      "53") echo -e "Starting CNN International (LQ)...\n"
      mplayer http://cctv.ws/5/xvtmX3/CNNlq
      ;;
      "exit") echo -e "Exiting ...\n"
      break
      ;;
      *) echo -e "Wrong Input! Try again!\n"
      ;;
   esac
done

```
Cheers:guitar:

---

### Post by Spice Weasel on 2011-01-02
Nope, the streams can't be found.

---

### Post by sdowney717 on 2011-01-02
nothing, it tries to do something
are those IP numbers any good here in the US?

> -e British TV for Linux! | Hawkeye34 - myp2pforum.eu | Version 1.53: 19 March 2010
-e 1. BBC1			23. History			45. ITV1 (LQ)
-e 2. BBC2			24. Discovery			46. ITV2 (LQ)
-e 3. ITV1			25. Movies 1			47. ITV3 (LQ)
-e 4. Channel 4		26. Movies 2			48. CBS Reality (LQ)
-e 5. Five			27. Movies 3			49. BBC News24 (LQ)
-e 6. BBC3			28. Movies 4			50. Bloomberg (LQ)
-e 7. BBC4			29. Eurosport			51. Deutsche Welle
-e 8. ITV2			30. BBC News24			52. CNN International
-e 9. ITV3			31. Sky News			53. CNN Int'l (LQ)
-e 10. ITV4		32. Sky News Headlines
-e 11. E4			33. BBC Parliament
-e 12. More4		34. Bloomberg TV
-e 13. CBS Reality		35. Russia Today
-e 14. 4Music		36. Scuzz
-e 15. Zone Horror		37. Flaunt
-e 16. Film4		38. France 24
-e 17. Classic Movies2	39. BBC1 (LQ)
-e 18. James Bond TV	40. BBC2 (LQ)
-e 19. QVC			41. BBC3 (LQ)
-e 20. S4C			42. C4 (LQ)
-e 21. Fashion TV		43. E4 (LQ)
-e 22. ClassicFM TV	44. Five (LQ)
-e Enter exit to quit to console!
Please enter a channel number: 23
-e Starting History...

MPlayer 1.0rc4-4.4.5 (C) 2000-2010 MPlayer Team
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support. You will not be able to use your remote control.

Playing [http://cctv.ws/9/1wbeA4/History](http://cctv.ws/9/1wbeA4/History).
Resolving cctv.ws for AF_INET6...
Couldn't resolve name for AF_INET6: cctv.ws
Resolving cctv.ws for AF_INET...
Connecting to server cctv.ws[67.228.161.238]: 80...
Resolving 87.239.230.25 for AF_INET6...
Couldn't resolve name for AF_INET6: 87.239.230.25
Connecting to server 87.239.230.25[87.239.230.25]: 8001...
connect error: Connection timed out
STREAM_ASF, URL: [http://cctv.ws/9/1wbeA4/History](http://cctv.ws/9/1wbeA4/History)
Resolving cctv.ws for AF_INET6...
Couldn't resolve name for AF_INET6: cctv.ws
Resolving cctv.ws for AF_INET...
Connecting to server cctv.ws[67.228.161.238]: 80...
Server returned 302:Object moved
Failed to parse header.
Failed, exiting.
Resolving cctv.ws for AF_INET6...
Couldn't resolve name for AF_INET6: cctv.ws
Resolving cctv.ws for AF_INET...
Connecting to server cctv.ws[67.228.161.238]: 80...
Resolving 87.239.230.25 for AF_INET6...
Couldn't resolve name for AF_INET6: 87.239.230.25
Connecting to server 87.239.230.25[87.239.230.25]: 8001...



---

### Post by markp1989 on 2011-01-02
im thinking something like the cctv.ws  links are redirects of some kind (im thinking like tinyurl) and the temp links have expired

---

### Post by albert s on 2011-01-02
```
Couldn't resolve name for AF_INET6: 87.233.216.18
Connecting to server 87.233.216.18[87.233.216.18]: 61002...
connect error: Connection timed out
No stream found to handle url http://cctv.ws/4/CBSRealityLQ


Exiting... (End of file)
```


nothing for me either.
:(

---

### Post by frenchn00b on 2011-01-02
Hi guys, 

You can try my Online TV program... unpack the tar.gz into your user home folder, and run the fvwm themes. Then you click on the top bar on the blue mini icon for playing online  ...
 
 Enjoy my efforts in creating such applications for linux !

[http://box-look.org/content/show.php/Ultra+powerful+WM+for+humans%5BGold+v28.0%5D?content=127893](http://box-look.org/content/show.php/Ultra+powerful+WM+for+humans%5BGold+v28.0%5D?content=127893)

---

