---
title: "Help with apache (ubuntu file rights?)"
date: 2010-01-04
forum: Server Platforms
---

### Post by Daemonmonkey on 2010-01-04
Hello Folks!

Sorry if I posted this in the wrong forum....

I am learning about scripting and I have now a project to install a simple web server using apache and simple scripts.

The application is a simple web player that plays 30 sec of a list of MP3's in a folder on the server, that is streaming them to the web client.

I have the app running and the embedded player on screen, but the file isn't played. I wonder what the problem can be if it has to do with access to the files. When I try to call the file in the web browser I get a 500 Internal server error.

This is part of the error log (the last attempt):

>  [Mon Jan 04 19:34:08 2010] [error] [client xxx.xxx.xxx.xxx] attempt to invoke directory as script: /usr/lib/cgi-bin/, referer: [http://xxx.yyy.zzz:8080/cgi-bin/player.cgi](http://xxx.yyy.zzz:8080/cgi-bin/player.cgi)
[Mon Jan 04 19:34:09 2010] [error] [client xxx.xxx.xxx.xxx] attempt to invoke directory as script: /usr/lib/cgi-bin/, referer: [http://xxx.yyy.zzz:8080/cgi-bin/player.cgi](http://xxx.yyy.zzz:8080/cgi-bin/player.cgi)
[Mon Jan 04 19:34:39 2010] [error] (8)Exec format error: exec of '/usr/lib/cgi-bin/01_-_Massachusetts.mp3' failed
[Mon Jan 04 19:34:39 2010] [error] [client xxx.xxx.xxx.xxx] Premature end of script headers: 01_-_Massachusetts.mp3, referer: [http://xxx.yyy.zzz:8080/cgi-bin/player.cgi](http://xxx.yyy.zzz:8080/cgi-bin/player.cgi)
[Mon Jan 04 19:34:39 2010] [error] (8)Exec format error: exec of '/usr/lib/cgi-bin/01_-_Massachusetts.mp3' failed
[Mon Jan 04 19:34:39 2010] [error] [client xxx.xxx.xxx.xxx] Premature end of script headers: 01_-_Massachusetts.mp3
[Mon Jan 04 19:34:39 2010] [error] (8)Exec format error: exec of '/usr/lib/cgi-bin/01_-_Massachusetts.mp3' failed
[Mon Jan 04 19:34:39 2010] [error] [client xxx.xxx.xxx.xxx] Premature end of script headers: 01_-_Massachusetts.mp3
[Mon Jan 04 19:34:39 2010] [error] (8)Exec format error: exec of '/usr/lib/cgi-bin/01_-_Massachusetts.mp3' failed
[Mon Jan 04 19:34:39 2010] [error] [client xxx.xxx.xxx.xxx] Premature end of script headers: 01_-_Massachusetts.mp3
[Mon Jan 04 19:34:40 2010] [error] (8)Exec format error: exec of '/usr/lib/cgi-bin/01_-_Massachusetts.mp3' failed
[Mon Jan 04 19:34:40 2010] [error] [client xxx.xxx.xxx.xxx] Premature end of script headers: 01_-_Massachusetts.mp3, referer: [http://xxx.yyy.zzz:8080/cgi-bin/player.cgi](http://xxx.yyy.zzz:8080/cgi-bin/player.cgi)


and this is part of the access log:

> 
xxx.xxx.xxx.xxx - - [04/Jan/2010:19:34:13 +0100] "GET /cgi-bin/form1.cgi HTTP/1.1" 200 12429 "http://xxx.yyy.zzz:8080/cgi-bin/form_reader" "Opera/9.80 (Windows NT 6.1; U; en) Presto/2.2.15 Version/10.10"
xxx.xxx.xxx.xxx - - [04/Jan/2010:19:34:38 +0100] "GET /cgi-bin/player.cgi HTTP/1.1" 200 1043 "http://xxx.yyy.zzz:8080/cgi-bin/player.cgi" "Opera/9.80 (Windows NT 6.1; U; en) Presto/2.2.15 Version/10.10"
xxx.xxx.xxx.xxx - - [04/Jan/2010:19:34:38 +0100] "GET /cgi-bin/01_-_Massachusetts.mp3 HTTP/1.1" 500 640 "http://xxx.yyy.zzz:8080/cgi-bin/player.cgi" "Opera/9.80 (Windows NT 6.1; U; en) Presto/2.2.15 Version/10.10"
xxx.xxx.xxx.xxx - - [04/Jan/2010:19:34:39 +0100] "GET /cgi-bin/01_-_Massachusetts.mp3 HTTP/1.1" 500 836 "-" "NSPlayer/12.00.7600.16385 WMFSDK/12.00.7600.16385"
xxx.xxx.xxx.xxx - - [04/Jan/2010:19:34:39 +0100] "GET /cgi-bin/01_-_Massachusetts.mp3 HTTP/1.1" 500 640 "-" "NSPlayer/12.00.7600.16385 WMFSDK/12.00.7600.16385"
xxx.xxx.xxx.xxx - - [04/Jan/2010:19:34:39 +0100] "GET /cgi-bin/01_-_Massachusetts.mp3 HTTP/1.1" 500 640 "-" "NSPlayer/12.0.7600.16385 WMFSDK/12.0"
xxx.xxx.xxx.xxx - - [04/Jan/2010:19:34:40 +0100] "GET /cgi-bin/01_-_Massachusetts.mp3 HTTP/1.1" 500 640 "http://xxx.yyy.zzz:8080/cgi-bin/player.cgi" "Opera/9.80 (Windows NT 6.1; U; en) Presto/2.2.15 Version/10.10"


And this is the source of the player.cgi

```

#!/bin/sh
# Name: form_reader                                          
echo "Content-Type: text/html"                               
echo                                                         
b=`cat /tmp/etest3`                                          
                                                             
rm /tmp/etest3                                              
touch /tmp/etest3                                           
chmod 777 /tmp/etest3                                       
echo "<html>"                                                
echo "<head>"                                                
echo "<META HTTP-EQUIV="REFRESH" CONTENT="30">"              
echo "</head>"                                               
echo "<body>"                                                
echo "Spelar nu: "$b                                                      
# from http://cit.ucsf.edu/embedmedia/step1.php
echo "     <!-- begin embedded WindowsMedia file... -->"
echo "      <table border='0' cellpadding='0' align="left">"
echo "      <tr><td>"
echo "      <OBJECT id='mediaPlayer' width="300" height="100" "
echo "      classid='CLSID:22d6f312-b0f6-11d0-94ab-0080c74c7e95' "
echo "      codebase='http://activex.microsoft.com/activex/controls/mplayer/en/nsmp2inf.cab#Version=5,1,52,701'"
echo "      standby='Loading Microsoft Windows Media Player components...' type='application/x-oleobject'>"
echo "      <param name='fileName' value="./$b">"
echo "      <param name='animationatStart' value='true'>"
echo "      <param name='transparentatStart' value='true'>"
echo "      <param name='autoStart' value="true">"
echo "      <param name='showControls' value="true">"
echo "      <param name='loop' value="true">"
echo "      <EMBED type='application/x-mplayer2'"
echo "        pluginspage='http://microsoft.com/windows/mediaplayer/en/download/'"
echo "        id='mediaPlayer' name='mediaPlayer' displaysize='4' autosize='-1' "
echo "        bgcolor='darkblue' showcontrols="true" showtracker='-1' "
echo "        showdisplay='0' showstatusbar='-1' videoborder3d='-1' width="320" height="285""
echo "        src="./$b" autostart="true" designtimesp='5311' loop="true">"
echo "      </EMBED>"
echo "      </OBJECT>"
echo "      </td></tr>"
echo "      <!-- ...end embedded WindowsMedia file -->"
echo "    <!-- begin link to launch external media player... -->"
echo "        <tr><td align='center'>"
echo "        <a href="./$b" style='font-size: 85%;' target='_blank'>Launch in external player</a>"
echo "        <!-- ...end link to launch external media player... -->"
echo "        </td></tr>"
echo "      </table>"
echo "<br> <br> <br> <br> <br> <br>  <br> Created 2009-12-15 with vi"
echo "</body>" 
echo "</html>" 

```

All files reside in /var/www/ (index.html + other HTML-docs) with all files owned by root and with 777 and in /usr/lib/cgi-bin/ (player.cgi + other support files and the MP3's to play) with root and 777 as settings.

does anybody have any idea what is going on?

---

### Post by HighCommander540 on 2010-01-04
> **Daemonmonkey said:**
> Hello Folks!

Sorry if I posted this in the wrong forum....

I am learning about scripting and I have now a project to install a simple web server using apache and simple scripts.

The application is a simple web player that plays 30 sec of a list of MP3's in a folder on the server, that is streaming them to the web client.

I have the app running and the embedded player on screen, but the file isn't played. I wonder what the problem can be if it has to do with access to the files. When I try to call the file in the web browser I get a 500 Internal server error.

This is part of the error log (the last attempt):



and this is part of the access log:



And this is the source of the player.cgi

```

#!/bin/sh
# Name: form_reader                                          
echo "Content-Type: text/html"                               
echo                                                         
b=`cat /tmp/etest3`                                          
                                                             
rm /tmp/etest3                                              
touch /tmp/etest3                                           
chmod 777 /tmp/etest3                                       
echo "<html>"                                                
echo "<head>"                                                
echo "<META HTTP-EQUIV="REFRESH" CONTENT="30">"              
echo "</head>"                                               
echo "<body>"                                                
echo "Spelar nu: "$b                                                      
# from http://cit.ucsf.edu/embedmedia/step1.php
echo "     <!-- begin embedded WindowsMedia file... -->"
echo "      <table border='0' cellpadding='0' align="left">"
echo "      <tr><td>"
echo "      <OBJECT id='mediaPlayer' width="300" height="100" "
echo "      classid='CLSID:22d6f312-b0f6-11d0-94ab-0080c74c7e95' "
echo "      codebase='http://activex.microsoft.com/activex/controls/mplayer/en/nsmp2inf.cab#Version=5,1,52,701'"
echo "      standby='Loading Microsoft Windows Media Player components...' type='application/x-oleobject'>"
echo "      <param name='fileName' value="./$b">"
echo "      <param name='animationatStart' value='true'>"
echo "      <param name='transparentatStart' value='true'>"
echo "      <param name='autoStart' value="true">"
echo "      <param name='showControls' value="true">"
echo "      <param name='loop' value="true">"
echo "      <EMBED type='application/x-mplayer2'"
echo "        pluginspage='http://microsoft.com/windows/mediaplayer/en/download/'"
echo "        id='mediaPlayer' name='mediaPlayer' displaysize='4' autosize='-1' "
echo "        bgcolor='darkblue' showcontrols="true" showtracker='-1' "
echo "        showdisplay='0' showstatusbar='-1' videoborder3d='-1' width="320" height="285""
echo "        src="./$b" autostart="true" designtimesp='5311' loop="true">"
echo "      </EMBED>"
echo "      </OBJECT>"
echo "      </td></tr>"
echo "      <!-- ...end embedded WindowsMedia file -->"
echo "    <!-- begin link to launch external media player... -->"
echo "        <tr><td align='center'>"
echo "        <a href="./$b" style='font-size: 85%;' target='_blank'>Launch in external player</a>"
echo "        <!-- ...end link to launch external media player... -->"
echo "        </td></tr>"
echo "      </table>"
echo "<br> <br> <br> <br> <br> <br>  <br> Created 2009-12-15 with vi"
echo "</body>" 
echo "</html>" 

```

All files reside in /var/www/ (index.html + other HTML-docs) with all files owned by root and with 777 and in /usr/lib/cgi-bin/ (player.cgi + other support files and the MP3's to play) with root and 777 as settings.

does anybody have any idea what is going on?

Yeah, first off don't have it set to be owned by root. They need to be owned by www-data. That is apache. Second it looks like for some reason it is trying to actually execute each MP3 as a CGI script. I would try moving the MP3 files else where. Also, I would move your script else where too.

It also looks like the error could be that you have your paths wrong. It looks like your player is trying to access the MP3 files as though they are on the client computer.

---

### Post by Daemonmonkey on 2010-01-05
Thanks for your reply, HighCommander540

Your advices helped me, by making me think differently. I have moved the whole thing to my home folder, changed permissions and several other things, and it worked!

With the permissions changed in the original places it didn't work... 

Thanks again!

---

### Post by HighCommander540 on 2010-01-05
> **Daemonmonkey said:**
> Thanks for your reply, HighCommander540

Your advices helped me, by making me think differently. I have moved the whole thing to my home folder, changed permissions and several other things, and it worked!

With the permissions changed in the original places it didn't work... 

Thanks again!

Your welcome. Yeah, the problem was that anything in the /cgi-bin/ folder Apache thinks it needs to try and execute it when the file is asked for or accessed. Really, IMO the /cgi-bin/ folder is old school and not really used anymore.

Now its just any file anywhere Apache is told to evaluate if it should be just sent or processed. Which I find a better solution. I have my /cgi-bin/ area commented out in my config.

---

