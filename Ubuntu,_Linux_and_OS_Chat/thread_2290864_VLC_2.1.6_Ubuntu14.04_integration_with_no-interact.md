---
title: "VLC 2.1.6 Ubuntu14.04 integration with no-interaction"
date: 2015-08-16
forum: Ubuntu, Linux and OS Chat
---

### Post by jooaik on 2015-08-16
---- xxx.sh file ------- chmod a+x ------
echo ##### for vlc script, chmod a+x is sufficient as vlc cannot run as root
echo #### add in command excution attribute to shell file "sh /home/pcname/Documents/foldername/xxx.sh"
echo #### in Startup Application for command shell sh to run
echo #### "sh /home/pcname/Documents/foldername/foldername/.sh"
echo #### m3u-0-main.m3u contains the playlist in standard format




echo ## hide launcher
[FONT=courier new]gsettings set org.compiz.unityshell:/org/compiz/profiles/unity/plugins/unityshell/ launcher-hide-mode 1[/FONT]


echo ## turn off shutdown/restart prompt
[FONT=courier new]gsettings set com.canonical.indicator.session suppress-logout-restart-shutdown true[/FONT]


echo ### delay to give time for network to be established, user can increase further if needed
[FONT=courier new]sleep 4[/FONT]


echo ### change path
[FONT=courier new]cd /home/pcname/Documents/foldername[/FONT]


echo ### connect to ftp server to get the latest playlist
echo ### use wget, -N is the best option, if playlist is new, overwrite
echo ### wget will try 2 times


## wget -A.m3u --user=ftpuser --password='ftppassword' [ftp://xxx.xx.xx.xx/ftppath-to-playlist/m3u-0-main.m3u](ftp://xxx.xx.xx.xx/ftppath-to-playlist/m3u-0-main.m3u) /home/pcname/Documents/foldername/m3u-0-main.m3u --tries=2 -q --output-document=m3u-0-main.m3u


[FONT=courier new]wget -A.m3u --user=ftpuser --password='ftppassword' [ftp://xxx.xx.xx.xx/ftppath-to-playlist/m3u-0-main.m3u](ftp://xxx.xx.xx.xx/ftppath-to-playlist/m3u-0-main.m3u) /home/pcname/Documents/foldername/m3u-0-main.m3u --tries=2 -q -N

[/FONT]
## wget -A.m3u --user=ftpuser --password='ftppassword' [ftp://xxx.xx.xx.xx/ftppath-to-playlist/m3u-0-main.m3u](ftp://xxx.xx.xx.xx/ftppath-to-playlist/m3u-0-main.m3u) /home/pcname/Documents/foldername/m3u-0-main.m3u --tries=2 -q -r -p




echo ### setup a delay in case FTP takes a while to connect 
[FONT=courier new]sleep 10[/FONT]


echo ### setup path
[FONT=courier new]cd /home/pcname/Documents/foldername[/FONT]


echo ### launch VLC in fullscreen, with playlist=m3u-0-main.m3u, audio=alsa, loop forever, quiet mode, only one instance, setup http access to forward playlist
[FONT=courier new]vlc file:///home/pcname/Documents/foldername/m3u-0-main.m3u --fullscreen --aout alsa --loop --quiet --one-instance --no-interact --extraintf=http --http-password httppassword [/FONT]
[FONT=courier new]exit 0[/FONT]


----end of --- xxx.sh file ------- -




--- m3u-0-main.m3u example ---
*[SIZE=2][FONT=courier new]#EXTM3U [/FONT][/SIZE]*
*[SIZE=2][FONT=courier new]#EXTVLCOPT:network-caching=4000 [/FONT][/SIZE]*
*[SIZE=2][FONT=courier new] [http://avenard.org/iptv/playlist-tpg-vlc.m3u](http://avenard.org/iptv/playlist-tpg-vlc.m3u)[/FONT][/SIZE]*
*[SIZE=2][FONT=courier new]#EXTINF:0,301 - Al Jazeera (English)[/FONT][/SIZE]*
*[SIZE=2][FONT=courier new] rtp://@233.29.121.2:1234[/FONT][/SIZE]*
*[SIZE=2][FONT=courier new] #EXTINF:0,302 - Bloomberg (English)[/FONT][/SIZE]*
*[SIZE=2][FONT=courier new] rtp://@233.29.121.3:1234[/FONT][/SIZE]*
*[SIZE=2][FONT=courier new] [http://www.yourtube.com/watch?v=abc1234](http://www.yourtube.com/watch?v=abc1234)[/FONT][/SIZE]*
*[SIZE=2][FONT=courier new] [https://www.example.com/stream.avi](https://www.example.com/stream.avi)[/FONT][/SIZE]*
*[SIZE=2][FONT=courier new] mms://203.113.9.83/Encoder11[/FONT][/SIZE]*
*[SIZE=2][FONT=courier new] [http://www.cnn.com/video/live/live.html?stream=stream1](http://www.cnn.com/video/live/live.html?stream=stream1)[/FONT][/SIZE]*
--- end of  m3u-0-main.m3u example --

---

