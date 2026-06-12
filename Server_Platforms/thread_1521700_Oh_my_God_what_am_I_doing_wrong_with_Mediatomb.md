---
title: "Oh my God what am I doing wrong with Mediatomb?"
date: 2010-07-01
forum: Server Platforms
---

### Post by Captain Smiley Pants on 2010-07-01
Alright, so I read about how amazing and quick and easy and awesome mediatomb is on these forums. Getting sick of dumping my video files onto my PS3, I decide to give it a try.

I let it run it's first session, let it create it's config file, then exit and edit the file accordingly. This is my current file:

```
<config version="1" xsi:schemaLocation="http://mediatomb.cc/config/1 http://mediatomb.cc/config/1.xsd">
&#8722;
<!--

     Read /usr/share/doc/mediatomb-common/README.gz section 6 for more
     information on creating and using config.xml configration files.
    
-->
&#8722;
<server>
&#8722;
<ui enabled="yes" show-tooltips="yes">
&#8722;
<accounts enabled="no" session-timeout="30">
<account user="mediatomb" password="mediatomb"/>
</accounts>
</ui>
<name>MediaTomb</name>
<udn>uuid:031fcee3-4964-4c3f-af32-cc1b5b780355</udn>
<home>/home/coleman/.mediatomb</home>
<webroot>/usr/share/mediatomb/web</webroot>
&#8722;
<storage>
&#8722;
<sqlite3 enabled="yes">
<database-file>mediatomb.db</database-file>
</sqlite3>
&#8722;
<mysql enabled="no">
<host>localhost</host>
<username>mediatomb</username>
<database>mediatomb</database>
</mysql>
</storage>
<protocolInfo extend="yes"/>
<!-- For PS3 support change to "yes" -->
&#8722;
<!--

       Uncomment the lines below to get rid of jerky avi playback on the
       DSM320 or to enable subtitles support on the DSM units
    
-->
&#8722;
<!--

    <custom-http-headers>
      <add header="X-User-Agent: redsonic"/>
    </custom-http-headers>

    <manufacturerURL>redsonic.com</manufacturerURL>
    <modelNumber>105</modelNumber>
    
-->
&#8722;
<!--
 Uncomment the line below if you have a Telegent TG100 
-->
&#8722;
<!--

       <upnp-string-limit>101</upnp-string-limit>
    
-->
&#8722;
<extended-runtime-options>
&#8722;
<ffmpegthumbnailer enabled="no">
<thumbnail-size>128</thumbnail-size>
<seek-percentage>5</seek-percentage>
<filmstrip-overlay>yes</filmstrip-overlay>
<workaround-bugs>no</workaround-bugs>
</ffmpegthumbnailer>
&#8722;
<mark-played-items enabled="no" suppress-cds-updates="yes">
<string mode="prepend">*</string>
</mark-played-items>
</extended-runtime-options>
</server>
&#8722;
<import hidden-files="no">
&#8722;
<scripting script-charset="UTF-8">
<virtual-layout type="builtin"/>
</scripting>
&#8722;
<mappings>
&#8722;
<extension-mimetype ignore-unknown="no">
<map from="mp3" to="audio/mpeg"/>
<map from="ogg" to="application/ogg"/>
<map from="asf" to="video/x-ms-asf"/>
<map from="asx" to="video/x-ms-asf"/>
<map from="wma" to="audio/x-ms-wma"/>
<map from="wax" to="audio/x-ms-wax"/>
<map from="wmv" to="video/x-ms-wmv"/>
<map from="wvx" to="video/x-ms-wvx"/>
<map from="wm" to="video/x-ms-wm"/>
<map from="wmx" to="video/x-ms-wmx"/>
<map from="m3u" to="audio/x-mpegurl"/>
<map from="pls" to="audio/x-scpls"/>
<map from="flv" to="video/x-flv"/>
<map from="mkv" to="video/x-matroska"/>
<map from="mka" to="audio/x-matroska"/>
<!-- Uncomment the line below for PS3 divx support -->
<map from="avi" to="video/divx"/>
&#8722;
<!--
 Uncomment the line below for D-Link DSM / ZyXEL DMA-1000 
-->
<!-- <map from="avi" to="video/avi"/> -->
</extension-mimetype>
&#8722;
<mimetype-upnpclass>
<map from="audio/*" to="object.item.audioItem.musicTrack"/>
<map from="video/*" to="object.item.videoItem"/>
<map from="image/*" to="object.item.imageItem"/>
<map from="application/ogg" to="object.item.audioItem.musicTrack"/>
</mimetype-upnpclass>
&#8722;
<mimetype-contenttype>
<treat mimetype="audio/mpeg" as="mp3"/>
<treat mimetype="application/ogg" as="ogg"/>
<treat mimetype="audio/x-flac" as="flac"/>
<treat mimetype="image/jpeg" as="jpg"/>
<treat mimetype="audio/x-mpegurl" as="playlist"/>
<treat mimetype="audio/x-scpls" as="playlist"/>
<treat mimetype="audio/x-wav" as="pcm"/>
<treat mimetype="audio/L16" as="pcm"/>
<treat mimetype="video/x-msvideo" as="avi"/>
<treat mimetype="video/mp4" as="mp4"/>
<treat mimetype="audio/mp4" as="mp4"/>
<treat mimetype="application/x-iso9660" as="dvd"/>
<treat mimetype="application/x-iso9660-image" as="dvd"/>
<treat mimetype="video/x-matroska" as="mkv"/>
<treat mimetype="audio/x-matroska" as="mka"/>
</mimetype-contenttype>
</mappings>
&#8722;
<online-content>
<!-- Make sure to setup a transcoding profile for flv -->
&#8722;
<YouTube enabled="no" refresh="28800" update-at-start="no" purge-after="604800" racy-content="exclude" format="flv" hd="no">
<favorites user="mediatomb"/>
<standardfeed feed="most_viewed" time-range="today"/>
<playlists user="mediatomb"/>
<uploads user="mediatomb"/>
<standardfeed feed="recently_featured" time-range="today"/>
</YouTube>
&#8722;
<Weborama enabled="no" refresh="28800" update-at-start="no">
<playlist name="Active" type="playlist" mood="active"/>
&#8722;
<playlist name="Metal" type="playlist">
&#8722;
<filter>
<genres>metal</genres>
</filter>
</playlist>
</Weborama>
<AppleTrailers enabled="no" refresh="43200" update-at-start="no" resolution="640"/>
</online-content>
</import>
&#8722;
<transcoding enabled="no">
&#8722;
<mimetype-profile-mappings>
<transcode mimetype="video/x-flv" using="vlcmpeg"/>
<transcode mimetype="application/ogg" using="vlcmpeg"/>
<transcode mimetype="application/ogg" using="oggflac2raw"/>
<transcode mimetype="audio/x-flac" using="oggflac2raw"/>
</mimetype-profile-mappings>
&#8722;
<profiles>
&#8722;
<profile name="oggflac2raw" enabled="no" type="external">
<mimetype>audio/L16</mimetype>
<accept-url>no</accept-url>
<first-resource>yes</first-resource>
<accept-ogg-theora>no</accept-ogg-theora>
<agent command="ogg123" arguments="-d raw -o byteorder:big -f %out %in"/>
<buffer size="1048576" chunk-size="131072" fill-size="262144"/>
</profile>
&#8722;
<profile name="vlcmpeg" enabled="no" type="external">
<mimetype>video/mpeg</mimetype>
<accept-url>yes</accept-url>
<first-resource>yes</first-resource>
<accept-ogg-theora>yes</accept-ogg-theora>
<agent command="vlc" arguments="-I dummy %in --sout #transcode{venc=ffmpeg,vcodec=mp2v,vb=4096,fps=25,aenc=ffmpeg,acodec=mpga,ab=192,samplerate=44100,channels=2}:standard{access=file,mux=ps,dst=%out} vlc:quit"/>
<buffer size="14400000" chunk-size="512000" fill-size="120000"/>
</profile>
</profiles>
</transcoding>
</config>
```

Seems simple for now, maybe I'll use VLC for encoding later. But that's not the focus right now, the focus is just getting the damn thing to be recognized by my PS3.

Fine, I'm sure there are more steps involved. So let's see, what else... Oh yes, I *am* running a wireless card! So, I kill the current mediatomb service and start a new one with this command:

[B]mediatomb -e wlan0 -d

[/B]I reset the PS3 and, welp, still can't read the server. Let's try this!

[B]sudo service mediatomb start

[/B]I get a confirmation message that yes, the service has started. Alright, I'll reset the PS3 again and... No cigar. Alright, let's see what else is going on... Oh yes! I should probably make sure the specific port I need it open in the router I'm using. Silly me.

Alright, I have port **49152 **forwarded! I'm just going to restart, well, everything at this point.

So I start the service again, specifying my NIC, running is as a daemon, and officially start the service. Then I turn on my PS3, do a search for media servers, and... nothing. Still nothing!

Maybe something really is wrong? I'll just type in the IP of my machine and the port and... Yeah, there's the information and the directory of all the stuff I want to stream.

OK, I know I'm about to screw up IPtables and I really don't want to, but drastic times call for drastic measures!

I install Firestarter. Oh God how I hate you Firestarter. Let's get this over with...

I start with no policies, outbound traffic is blacklist only and inbound has nothing. I check for any blocked traffic, and the log starts showing port 1900 and it's an SSDP service from 192.168.0.2 (at this point, I've statically assigned the PS3's IP address, just so I know where the hell my traffic is). So I allow the port for everyone (I know, bad idea, but I'm experimenting), and watch the log some more. In the mean time, I make sure that the host 192.168.0.2 is an allowed connection.

So when 0.2 tries to use the port I've opened, I allow the service. After a little while, I decide it's time for another reboot on everything, the PS3, the router, the netbook, *everything*.

I disable the splash screen so I know Firestarter and it's modified tables are running. I start mediatomb like I have been before.

I try using the PS3 again.

***NOTHING!***

No dice! At this point I have a pounding headache and am about ready for bed. Please, anyone, someone tell me I've missed a trivial step and I'm blowing things way out of proportion here!

I tried using uShare sometime during all of this. I managed to get it working, except I kept getting errors barfed back up from the PS3 and it could not find my documents for one reason or another. Which is another thing, before Ubuntu I had Vista on here with TVersity, and I know for sure my whole setup support upnp. So here I am.

Please, someone, please tell me this isn't all bad news! Maybe there is something, anything, more I could try?

---

### Post by Captain Smiley Pants on 2010-07-01
Alright, so I read about how amazing and quick and easy and awesome  mediatomb is on these forums. Getting sick of dumping my video files  onto my PS3, I decide to give it a try.

I let it run it's first session, let it create it's config file, then  exit and edit the file accordingly. This is my current file:

```
<config version="1"  xsi:schemaLocation="http://mediatomb.cc/config/1  http://mediatomb.cc/config/1.xsd">
&#8722;
<!--

     Read /usr/share/doc/mediatomb-common/README.gz section 6 for more
     information on creating and using config.xml configration files.
    
-->
&#8722;
<server>
&#8722;
<ui enabled="yes" show-tooltips="yes">
&#8722;
<accounts enabled="no" session-timeout="30">
<account user="mediatomb" password="mediatomb"/>
</accounts>
</ui>
<name>MediaTomb</name>
<udn>uuid:031fcee3-4964-4c3f-af32-cc1b5b780355</udn>
<home>/home/coleman/.mediatomb</home>
<webroot>/usr/share/mediatomb/web</webroot>
&#8722;
<storage>
&#8722;
<sqlite3 enabled="yes">
<database-file>mediatomb.db</database-file>
</sqlite3>
&#8722;
<mysql enabled="no">
<host>localhost</host>
<username>mediatomb</username>
<database>mediatomb</database>
</mysql>
</storage>
<protocolInfo extend="yes"/>
<!-- For PS3 support change to "yes" -->
&#8722;
<!--

       Uncomment the lines below to get rid of jerky avi playback on the
       DSM320 or to enable subtitles support on the DSM units
    
-->
&#8722;
<!--

    <custom-http-headers>
      <add header="X-User-Agent: redsonic"/>
    </custom-http-headers>

    <manufacturerURL>redsonic.com</manufacturerURL>
    <modelNumber>105</modelNumber>
    
-->
&#8722;
<!--
 Uncomment the line below if you have a Telegent TG100 
-->
&#8722;
<!--

       <upnp-string-limit>101</upnp-string-limit>
    
-->
&#8722;
<extended-runtime-options>
&#8722;
<ffmpegthumbnailer enabled="no">
<thumbnail-size>128</thumbnail-size>
<seek-percentage>5</seek-percentage>
<filmstrip-overlay>yes</filmstrip-overlay>
<workaround-bugs>no</workaround-bugs>
</ffmpegthumbnailer>
&#8722;
<mark-played-items enabled="no" suppress-cds-updates="yes">
<string mode="prepend">*</string>
</mark-played-items>
</extended-runtime-options>
</server>
&#8722;
<import hidden-files="no">
&#8722;
<scripting script-charset="UTF-8">
<virtual-layout type="builtin"/>
</scripting>
&#8722;
<mappings>
&#8722;
<extension-mimetype ignore-unknown="no">
<map from="mp3" to="audio/mpeg"/>
<map from="ogg" to="application/ogg"/>
<map from="asf" to="video/x-ms-asf"/>
<map from="asx" to="video/x-ms-asf"/>
<map from="wma" to="audio/x-ms-wma"/>
<map from="wax" to="audio/x-ms-wax"/>
<map from="wmv" to="video/x-ms-wmv"/>
<map from="wvx" to="video/x-ms-wvx"/>
<map from="wm" to="video/x-ms-wm"/>
<map from="wmx" to="video/x-ms-wmx"/>
<map from="m3u" to="audio/x-mpegurl"/>
<map from="pls" to="audio/x-scpls"/>
<map from="flv" to="video/x-flv"/>
<map from="mkv" to="video/x-matroska"/>
<map from="mka" to="audio/x-matroska"/>
<!-- Uncomment the line below for PS3 divx support -->
<map from="avi" to="video/divx"/>
&#8722;
<!--
 Uncomment the line below for D-Link DSM / ZyXEL DMA-1000 
-->
<!-- <map from="avi" to="video/avi"/> -->
</extension-mimetype>
&#8722;
<mimetype-upnpclass>
<map from="audio/*" to="object.item.audioItem.musicTrack"/>
<map from="video/*" to="object.item.videoItem"/>
<map from="image/*" to="object.item.imageItem"/>
<map from="application/ogg"  to="object.item.audioItem.musicTrack"/>
</mimetype-upnpclass>
&#8722;
<mimetype-contenttype>
<treat mimetype="audio/mpeg" as="mp3"/>
<treat mimetype="application/ogg" as="ogg"/>
<treat mimetype="audio/x-flac" as="flac"/>
<treat mimetype="image/jpeg" as="jpg"/>
<treat mimetype="audio/x-mpegurl" as="playlist"/>
<treat mimetype="audio/x-scpls" as="playlist"/>
<treat mimetype="audio/x-wav" as="pcm"/>
<treat mimetype="audio/L16" as="pcm"/>
<treat mimetype="video/x-msvideo" as="avi"/>
<treat mimetype="video/mp4" as="mp4"/>
<treat mimetype="audio/mp4" as="mp4"/>
<treat mimetype="application/x-iso9660" as="dvd"/>
<treat mimetype="application/x-iso9660-image" as="dvd"/>
<treat mimetype="video/x-matroska" as="mkv"/>
<treat mimetype="audio/x-matroska" as="mka"/>
</mimetype-contenttype>
</mappings>
&#8722;
<online-content>
<!-- Make sure to setup a transcoding profile for flv -->
&#8722;
<YouTube enabled="no" refresh="28800" update-at-start="no"  purge-after="604800" racy-content="exclude" format="flv" hd="no">
<favorites user="mediatomb"/>
<standardfeed feed="most_viewed" time-range="today"/>
<playlists user="mediatomb"/>
<uploads user="mediatomb"/>
<standardfeed feed="recently_featured" time-range="today"/>
</YouTube>
&#8722;
<Weborama enabled="no" refresh="28800" update-at-start="no">
<playlist name="Active" type="playlist" mood="active"/>
&#8722;
<playlist name="Metal" type="playlist">
&#8722;
<filter>
<genres>metal</genres>
</filter>
</playlist>
</Weborama>
<AppleTrailers enabled="no" refresh="43200" update-at-start="no"  resolution="640"/>
</online-content>
</import>
&#8722;
<transcoding enabled="no">
&#8722;
<mimetype-profile-mappings>
<transcode mimetype="video/x-flv" using="vlcmpeg"/>
<transcode mimetype="application/ogg" using="vlcmpeg"/>
<transcode mimetype="application/ogg" using="oggflac2raw"/>
<transcode mimetype="audio/x-flac" using="oggflac2raw"/>
</mimetype-profile-mappings>
&#8722;
<profiles>
&#8722;
<profile name="oggflac2raw" enabled="no" type="external">
<mimetype>audio/L16</mimetype>
<accept-url>no</accept-url>
<first-resource>yes</first-resource>
<accept-ogg-theora>no</accept-ogg-theora>
<agent command="ogg123" arguments="-d raw -o byteorder:big -f %out  %in"/>
<buffer size="1048576" chunk-size="131072" fill-size="262144"/>
</profile>
&#8722;
<profile name="vlcmpeg" enabled="no" type="external">
<mimetype>video/mpeg</mimetype>
<accept-url>yes</accept-url>
<first-resource>yes</first-resource>
<accept-ogg-theora>yes</accept-ogg-theora>
<agent command="vlc" arguments="-I dummy %in --sout  #transcode{venc=ffmpeg,vcodec=mp2v,vb=4096,fps=25,aenc=ffmpeg,acodec=mpga,ab=192,samplerate=44100,channels=2}:standard{access=file,mux=ps,dst=%out}  vlc:quit"/>
<buffer size="14400000" chunk-size="512000" fill-size="120000"/>
</profile>
</profiles>
</transcoding>
</config>
```Seems simple for now, maybe I'll use VLC for  encoding later. But that's not the focus right now, the focus is just  getting the damn thing to be recognized by my PS3.

Fine, I'm sure there are more steps involved. So let's see, what else...  Oh yes, I *am* running a wireless card! So, I kill the current  mediatomb service and start a new one with this command:

[B]mediatomb -e wlan0 -d

[/B]I reset the PS3 and, welp, still can't read the server. Let's try  this!

[B]sudo service mediatomb start

[/B]I get a confirmation message that yes, the service has started.  Alright, I'll reset the PS3 again and... No cigar. Alright, let's see  what else is going on... Oh yes! I should probably make sure the  specific port I need it open in the router I'm using. Silly me.

Alright, I have port **49152 **forwarded! I'm just going to restart,  well, everything at this point.

So I start the service again, specifying my NIC, running is as a daemon,  and officially start the service. Then I turn on my PS3, do a search  for media servers, and... nothing. Still nothing!

Maybe something really is wrong? I'll just type in the IP of my machine  and the port and... Yeah, there's the information and the directory of  all the stuff I want to stream.

OK, I know I'm about to screw up IPtables and I really don't want to,  but drastic times call for drastic measures!

I install Firestarter. Oh God how I hate you Firestarter. Let's get this  over with...

I start with no policies, outbound traffic is blacklist only and inbound  has nothing. I check for any blocked traffic, and the log starts  showing port 1900 and it's an SSDP service from 192.168.0.2 (at this  point, I've statically assigned the PS3's IP address, just so I know  where the hell my traffic is). So I allow the port for everyone (I know,  bad idea, but I'm experimenting), and watch the log some more. In the  mean time, I make sure that the host 192.168.0.2 is an allowed  connection.

So when 0.2 tries to use the port I've opened, I allow the service.  After a little while, I decide it's time for another reboot on  everything, the PS3, the router, the netbook, *everything*.

I disable the splash screen so I know Firestarter and it's modified  tables are running. I start mediatomb like I have been before.

I try using the PS3 again.

***NOTHING!***

No dice! At this point I have a pounding headache and am about ready for  bed. Please, anyone, someone tell me I've missed a trivial step and I'm  blowing things way out of proportion here!

I tried using uShare sometime during all of this. I managed to get it  working, except I kept getting errors barfed back up from the PS3 and it  could not find my documents for one reason or another. Which is another  thing, before Ubuntu I had Vista on here with TVersity, and I know for  sure my whole setup support upnp. So here I am.

Please, someone, please tell me this isn't all bad news! Maybe there is  something, anything, more I could try?

---

### Post by Captain Smiley Pants on 2010-07-01
bumpin' cuz i can't give up

---

### Post by littlegreiger on 2010-07-01
Do you have another computer on your network? If you do, check to see if that computer can see mediatomb. If it can't then it's a network problem, if it can then it might be a problem with your config file.

I glanced over your config file and compared it to the one I'm using right now and it doesn't look like there's much of a difference. I'm using a specific virtual layout instead of the builtin ones and I'm using mysql instead of sqlite. These shouldn't change anything though.

If you want to try another streaming server I'd suggest looking at [PS3 Mediaserver]("http://code.google.com/p/ps3mediaserver/"). I haven't used it on linux but I've used it on windows and it works great, right out of the box. Maybe take a look at it if you can't get mediatomb to work.

Best of luck.

---

### Post by CharlesA on 2010-07-01
Make sure that you don't have any firewall settings blocking the port that MediaTomb uses.

---

### Post by cariboo on 2010-07-02
Please don't create multiple threads on the same subject, I have merged your two threads.

---

