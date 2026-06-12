---
title: "Howto: Transcode on-the-fly to Xbox 360 with fuppes."
date: 2007-10-30
forum: Tutorials
---

### Post by Canute on 2007-10-30
This has been tested with a new version of Linux Mint Daryna (based on Gutsy), I've also tested that it compiles with a fresh version of Ubuntu Gutsy.

[SIZE="5"]Installation[/SIZE]
This part is the same if you have an xbox 360, a PS3 or any other upnp enabled media device.

We're going to use the very latest FUPPES release. To get transcoding to work, first we'll need ffmpeg.

Update your repositories ;)
```
$ sudo apt-get update
```

Install the files needed :)
```
$ sudo apt-get install ffmpeg build-essential \
libavutil-dev libavformat-dev libavcodec-dev \
subversion libtool automake autoconf \
libsqlite3-dev libpcre3-dev libxml2-dev
```

OPTIONAL:
This should work on videotranscoding, however, it doesn't install support for audio-transcoding (not video sound, that is handled by ffmpeg).
```
$ sudo apt-get install liblame-dev
```

Actually download and compile FUPPES:
```
$ svn co http://fuppes-svn.ulrich-voelkel.de/trunk fuppes
$ cd fuppes
$ autoreconf -vfi
$ ./configure --enable-video-transcoding
$ make
$ sudo make install
$ sudo ldconfig
```

[SIZE="5"]Configuration[/SIZE]
This part I can't help you with unless you have an xbox. Please go to [fuppes' site](http://fuppes.ulrich-voelkel.de/) for information about other devices. 

Open up /home/username/.fuppes/fuppes.cfg .
Add some directories to share
```
  <shared_objects>
    <dir>/home/user/myMedia</dir>
    <dir>/home/user/moreMedia</dir>
  </shared_objects>
```

Set the http port and interface to listen to:
```
  <network>
    <interface>eth1</interface>
    <http_port>8080</http_port>
  </network>
```
Scroll down till you find *<device name="Xbox 360" virtual="Xbox 360" enabled="false">*
Replace this section (up untill the next </device>) with this piece of text:
```
    <device name="Xbox 360" virtual="Xbox 360" enabled="true">
        <user_agent>Xbox/2.0.\d+.\d+ UPnP/1.0 Xbox/2.0.\d+.\d+</user_agent>
        <user_agent>Xenon</user_agent>
        <xbox360>true</xbox360>
        <file_settings>
            <file ext="mp3"><type>AUDIO_ITEM_MUSIC_TRACK</type></file>
            <file ext="jpg"><type>IMAGE_ITEM_PHOTO</type></file>
            <file ext="avi">
              <type>VIDEO_ITEM</type>
              <mime_type>video/x-msvideo</mime_type>
              <transcode enabled="true">         
                <transcoder>ffmpeg</transcoder>
                <ext>wmv</ext>
                <mime_type>video/x-ms-wmv</mime_type>         
                <video_codec>wmv2</video_codec>
                <audio_codec>wmav1</audio_codec>
                <video_bitrate>1800000</video_bitrate>
                <audio_bitrate>128000</audio_bitrate>
              </transcode>
            </file>
        </file_settings>
    </device>
```
You can change the video bitrate if you want. Personally, I think it's okay, but you want something higher just edit it.
Here's my fuppes.cfg for a reference: [http://canutes.net/fuppes/2/fuppes.cfg](http://canutes.net/fuppes/2/fuppes.cfg)

Download my vfolder.cfg and put it in the same directory as fuppes.cfg:
[http://canutes.net/fuppes/2/vfolder.cfg](http://canutes.net/fuppes/2/vfolder.cfg)

After you've started fuppes you should be able to open firefox at http://127.0.0.1:<your http port> and configure some there too, but I personally like just using the command line.


[SIZE="5"]Running[/SIZE]
Due to the early nature of fuppes, I have yet to find a good implemented solution for having it run as a daemon. Therefor I just run it as my own user.
```
$ fuppes
```
To build the database press 'r' then press 'v' to update the virtual folders. Now just connect your xbox 360 :D

---

### Post by lmellor on 2007-12-02
Hi, I have followed your instructions to the T but still my 360 cannot find my computer, I am admittedly quite a newbie to the wonderful world of ubuntu (and linux for that matter).  I have configured mine to use port 9452, I've setup shares, vfolders, etc.

I can see the web interface fine, my 360 just cannot find it for some reason.

Port forwarding is setup on my router to allow tcp and udp through the correct port to my static IP (on my ubuntu box).

Any suggestions are welcomed as I cannot wait to get this running, I'm pretty sure this is all that I am currently missing from the days of windows.

Thanks in advance.

---

### Post by lmellor on 2007-12-02
here is the transcript of what happens....

```
luke@UPSTAIRS:~/fuppes$ fuppes
            FUPPES - SVN-r571
    the Free UPnP Entertainment Service
      [http://fuppes.ulrich-voelkel.de](http://fuppes.ulrich-voelkel.de)

webinterface: [http://192.168.0.2:9452](http://192.168.0.2:9452)

r = rebuild database
i = print system info
h = print help

press "ctrl-c" or "q" to quit

:1: parser warning : xmlns:ms: ' urn:microsoft-com:wmc-1-0' is not a valid URI
ot xmlns="urn:schemas-upnp-org:device-1-0" xmlns:ms=" urn:microsoft-com:wmc-1-0"
                                                                               ^
== lib/Fuppes.cpp (336) :: Sun Dec  2 16:58:09 2007 ==
new device: Xbox 360 :: MediaRenderer

new UPnP device:
Xbox 360 (MediaRenderer)
```



here is my fuppes.cfg file...

```
<?xml version="1.0" encoding="UTF-8"?>
<fuppes_config version="0.7.2.3">
  <shared_objects>
    <!--<dir>/mnt/music</dir>-->
    <!--<itunes>/Users/.../iTunes.xml</itunes>-->
    <dir>/media/sda6/Music</dir>
    <dir>/media/sda6/Large Music Vids</dir>
  </shared_objects>

  <network>
    <!--empty = automatic detection-->
    <interface>eth0</interface>
    <!--empty or 0 = random port-->
    <http_port>9452</http_port>
    <!--list of ip addresses allowed to access fuppes. if empty all ips are allowed-->
    <allowed_ips>
      <!--<ip>192.168.0.1</ip>-->
      <ip>192.168.0.63</ip>
    </allowed_ips>
  </network>
  <content_directory>
    <!--a list of possible charsets can be found under:
      http://www.gnu.org/software/libiconv/-->
    <local_charset>UTF-8</local_charset>
    <!--libs used for metadata extraction when building the database. [true|false]-->
    <use_imagemagick>true</use_imagemagick>
    <use_taglib>true</use_taglib>
    <use_libavformat>true</use_libavformat>
  </content_directory>
  <transcoding>
    <!--[lame|twolame]-->
    <audio_encoder>lame</audio_encoder>
    <!--[true|false]-->
    <transcode_vorbis>true</transcode_vorbis>
    <transcode_musepack>true</transcode_musepack>
    <transcode_flac>true</transcode_flac>
  </transcoding>
  <device_settings>
    <!--"default" settings are inhertied by specific devices and can be overwritten-->
    <device name="default">
      <!--specify the maximum length for file names (0 or empty = unlimited)-->
      <max_file_name_length>0</max_file_name_length>
      <!--[file|container]-->
      <playlist_style>file</playlist_style>
      <show_childcount_in_title>false</show_childcount_in_title>
      <enable_dlna>false</enable_dlna>
      <transcoding_release_delay>4</transcoding_release_delay>
      <file_settings>
        <!--audio files-->
        <file ext="mp3">
          <type>AUDIO_ITEM</type>
          <mime_type>audio/mpeg</mime_type>
          <dlna>MP3</dlna>
        </file>
        <file ext="ogg">
          <type>AUDIO_ITEM</type>
          <mime_type>application/octet-stream</mime_type>
          <transcode enabled="true">
            <ext>mp3</ext>
            <mime_type>audio/mpeg</mime_type>
            <dlna>MP3</dlna>
            <http_encoding>chunked</http_encoding>
            <decoder>vorbis</decoder>
            <encoder>lame</encoder>
            <bitrate>192</bitrate>
            <samplerate>44100</samplerate>
          </transcode>
        </file>
        <file ext="mpc">
          <type>AUDIO_ITEM</type>
          <mime_type>application/octet-stream</mime_type>
          <transcode enabled="true">
            <ext>mp3</ext>
            <mime_type>audio/mpeg</mime_type>
            <dlna>MP3</dlna>
            <http_encoding>chunked</http_encoding>
            <decoder>musepack</decoder>
            <encoder>lame</encoder>
            <bitrate>192</bitrate>
            <samplerate>44100</samplerate>
          </transcode>
        </file>
        <file ext="wav">
          <type>AUDIO_ITEM</type>
          <mime_type>audio/x-wav</mime_type>
        </file>
        <file ext="flac">
          <type>AUDIO_ITEM</type>
          <mime_type>audio/x-flac</mime_type>
          <transcode enabled="true">
            <ext>mp3</ext>
            <mime_type>audio/mpeg</mime_type>
            <dlna>MP3</dlna>
            <http_encoding>chunked</http_encoding>
            <decoder>flac</decoder>
            <encoder>lame</encoder>
            <bitrate>192</bitrate>
            <samplerate>44100</samplerate>
          </transcode>
        </file>
        <file ext="wma">
          <type>AUDIO_ITEM</type>
          <mime_type>audio/x-ms-wma</mime_type>
          <dlna>WMAFULL</dlna>
        </file>
        <!--image files-->
        <file ext="jpg">
          <ext>jpeg</ext>
          <type>IMAGE_ITEM</type>
          <mime_type>image/jpeg</mime_type>
          <convert enabled="false">
            <!--<dcraw enabled="true">-q 0</dcraw>-->
            <ext>png</ext>
            <mime_type>image/png</mime_type>
            <height>0</height>
            <width>0</width>
            <!--set "greater" to "true" if you only want to resize images greater than "height" or "width"-->
            <greater>false</greater>
            <!--set "less" to "true" if you only want to resize images less than "height" or "width"-->
            <less>false</less>
            <!--set "less" and "greater" to "false" if you always want to resize-->
          </convert>
        </file>
        <file ext="bmp">
          <type>IMAGE_ITEM</type>
          <mime_type>image/bmp</mime_type>
        </file>
        <file ext="png">
          <type>IMAGE_ITEM</type>
          <mime_type>image/png</mime_type>
        </file>
        <file ext="gif">
          <type>IMAGE_ITEM</type>
          <mime_type>image/gif</mime_type>
        </file>
        <!--video files-->
        <file ext="mpg">
          <ext>mpeg</ext>
          <type>VIDEO_ITEM</type>
          <mime_type>video/mpeg</mime_type>
        </file>
        <file ext="mp4">
          <type>VIDEO_ITEM</type>
          <mime_type>video/mp4</mime_type>
        </file>
        <file ext="avi">
          <type>VIDEO_ITEM</type>
          <mime_type>video/x-msvideo</mime_type>
        </file>
        <file ext="wmv">
          <type>VIDEO_ITEM</type>
          <mime_type>video/x-ms-wmv</mime_type>
        </file>
        <file ext="vob">
          <type>VIDEO_ITEM</type>
          <mime_type>video/x-ms-vob</mime_type>
        </file>
        <file ext="vdr">
          <type>VIDEO_ITEM</type>
          <mime_type>video/x-extension-vdr</mime_type>
          <transcode enabled="true">
            <ext>vob</ext>
            <mime_type>video/x-ms-vob</mime_type>
          </transcode>
        </file>
        <file ext="flv">
          <type>VIDEO_ITEM</type>
          <mime_type>application/x-flash-video</mime_type>
        </file>
        <file ext="asf">
          <type>VIDEO_ITEM</type>
          <mime_type>video/x-ms-asf</mime_type>
        </file>
        <!--playlists-->
        <file ext="pls">
          <type>PLAYLIST</type>
          <mime_type>audio/x-scpls</mime_type>
        </file>
        <file ext="m3u">
          <type>PLAYLIST</type>
          <mime_type>audio/x-mpegurl</mime_type>
        </file>
      </file_settings>
    </device>
    <!--If you have more than one device it is a good idea to set the ip address manually as some devices may have conflicting "user agents".-->
    <device name="PS3" enabled="false">
      <user_agent>UPnP/1.0 DLNADOC/1.00</user_agent>
      <user_agent>PLAYSTATION3</user_agent>
      <!--<ip></ip>-->
      <enable_dlna>true</enable_dlna>
      <transcoding_release_delay>50</transcoding_release_delay>
      <file_settings>
        <file ext="ogg">
          <type>AUDIO_ITEM_MUSIC_TRACK</type>
          <transcode enabled="true">
            <http_encoding>stream</http_encoding>
          </transcode>
        </file>
      </file_settings>
    </device>
    <device name="Xbox 360" virtual="Xbox 360" enabled="true">
        <user_agent>Xbox/2.0.\d+.\d+ UPnP/1.0 Xbox/2.0.\d+.\d+</user_agent>
        <user_agent>Xenon</user_agent>
        <xbox360>true</xbox360>
        <file_settings>
            <file ext="mp3"><type>AUDIO_ITEM_MUSIC_TRACK</type></file>
            <file ext="jpg"><type>IMAGE_ITEM_PHOTO</type></file>
            <file ext="avi">
              <type>VIDEO_ITEM</type>
              <mime_type>video/x-msvideo</mime_type>
              <transcode enabled="true">         
                <transcoder>ffmpeg</transcoder>
                <ext>wmv</ext>
                <mime_type>video/x-ms-wmv</mime_type>         
                <video_codec>wmv2</video_codec>
                <audio_codec>wmav1</audio_codec>
                <video_bitrate>1800000</video_bitrate>
                <audio_bitrate>128000</audio_bitrate>
              </transcode>
            </file>
        </file_settings>
    </device>
    <device name="Telegent TG 100" virtual="default" enabled="false">
      <user_agent>dma/1.0 \(http://www.cybertan.com.tw/\)</user_agent>
      <user_agent>UPnP/1.0 DLNADOC/1.00</user_agent>
      <playlist_style>file</playlist_style>
      <max_file_name_length>101</max_file_name_length>
    </device>
  </device_settings>
</fuppes_config>
```


and here is my vfolder.cfg file...

```
<?xml version="1.0" encoding="UTF-8"?>
<fuppes_vfolder_config version="0.2">

 <vfolder_layout device="default" enabled="false">

    <vfolder name="Genre">
      <vfolders property="genre">
        <items type="audioItem" />
      </vfolders>
    </vfolder>

    <vfolder name="Genre/Artists">
      <vfolders property="genre">
        <vfolders property="artist">
          <items type="audioItem" />
        </vfolders>
      </vfolders>
    </vfolder>

    <vfolder name="Artists/Albums">
      <vfolders property="artist">
        <vfolders property="album">
          <items type="audioItem" />
        </vfolders>
      </vfolders>
    </vfolder> 
    
    <vfolder name="ABC/Artists/Albums">
      <vfolders split="ABC">
        <vfolders property="artist">
          <vfolders property="album">
            <items type="audioItem" />
          </vfolders>
        </vfolders>
      </vfolders>
    </vfolder>
       
    <vfolder name="Photos">
      <vfolder name="All">
        <items type="imageItem" />
      </vfolder>
      <vfolder name="Folders">
        <folders filter="contains(imageItem)" />
      </vfolder>      
    </vfolder>

    <vfolder name="Videos">
      <vfolder name="All">
        <items type="videoItem" />
      </vfolder>
      <vfolder name="Folders">
        <folders filter="contains(videoItem)" />
      </vfolder>
    </vfolder>
    
    <vfolder name="shared dirs">
      <shared_dirs full_extend="true" />
    </vfolder>
    
  </vfolder_layout>

  <vfolder_layout device="Xbox 360" enabled="true">

    <vfolder name="Music" id="1">
      <vfolder name="Album" id="7">
        <vfolders property="album" type="container.album.musicAlbum">
          <items type="audioItem" />
        </vfolders>
      </vfolder>
            
      <vfolder name="All Music" id="4">
        <items type="audioItem" />
      </vfolder>
      
      <vfolder name="Artist" id="6">
        <vfolders property="artist" type="container.person.musicArtist">
          <items type="audioItem" />
        </vfolders>
      </vfolder>
      
      <vfolder name="Folders" id="20">
        <folders filter="contains(audioItem)" />
      </vfolder>
      
      <vfolder name="Genre" id="5">
        <vfolders property="genre" type="container.genre.musicGenre">
          <items type="audioItem" />
        </vfolders>
      </vfolder>
      
      <vfolder name="Playlist" id="15" />
    </vfolder>
   
    <vfolder name="Pictures" id="3">
      <vfolder name="Album" id="13" />
      
      <vfolder name="All Pictures" id="11">
        <items type="imageItem" />
      </vfolder>
      
      <vfolder name="Date Taken" id="12" />
      
      <vfolder name="Folders" id="22">
        <folders filter="contains(imageItem)" />
      </vfolder>
    </vfolder>

    <vfolder name="Playlists" id="18">
      <vfolder name="All Playlists" id="19" />
      <vfolder name="Folders" id="23" />
    </vfolder>

    <vfolder name="Video" id="2">
      <vfolder name="Actor" id="10">
        <folders filter="contains(videoItem)" />
      </vfolder>
      <vfolder name="Album" id="14" />
      <vfolder name="All Video" id="8">
				<items type="videoItem" />
			</vfolder>
      <vfolder name="Folders" id="21">
			   <folders filter="contains(videoItem)" />
      </vfolder>
      <vfolder name="Genre" id="9" />
    </vfolder>

  </vfolder_layout>

</fuppes_vfolder_config>
```


I hope this helps somehow.

(I am running 64 bit gutsy btw)

---

### Post by lmellor on 2007-12-04
For anybody who is at the same point as I was then the answer lies in this thread...

[http://ubuntuforums.org/showthread.php?t=618781]("http://ubuntuforums.org/showthread.php?t=618781")

Thankfully somebody knew what was wrong and more importantly how to fix it!

---

### Post by durand on 2007-12-04
Nice howto.

If anyone's interested, this is my PS3 config(taken from the wiki and modified:

 > <device name="PS3" enabled="true">
      <user_agent>UPnP/1.0 DLNADOC/1.00</user_agent>
      <user_agent>PLAYSTATION3</user_agent>
<ip><ps3's ip></ip>
      <enable_dlna>true</enable_dlna>
      <transcoding_release_delay>50</transcoding_release_delay>
      <file_settings>
<file ext="ogg">
 <type>AUDIO_ITEM_MUSIC_TRACK</type>
  <mime_type>application/octet-stream</mime_type>
  <transcode enabled="true">
    <ext>mp3</ext>
    <mime_type>audio/mpeg</mime_type>
    <dlna>MP3</dlna>
    <http_encoding>stream</http_encoding>
    <decoder>vorbis</decoder>
    <encoder>lame</encoder>
    <bitrate>256</bitrate>
    <samplerate>44100</samplerate>
<transcoding_release_delay>60</transcoding_release_delay>
  </transcode>
</file>
	<file ext="flv">
	  <type>VIDEO_ITEM</type>
	  <mime_type>application/x-flash-video</mime_type>
	  <transcode enabled="true">
	    <ext>mpg</ext>
	    <mime_type>video/mpeg</mime_type>
	    <transcoder>ffmpeg</transcoder>     
	    <video_codec>mpeg1video</video_codec>
	    <audio_codec>mp2</audio_codec>
	    <audio_samplerate>44100</audio_samplerate>             
	    <video_bitrate>1800000</video_bitrate>
	  </transcode>
	</file>
	<file ext="mp4">
	  <type>VIDEO_ITEM_MOVIE</type>
	  <mime_type>video/mpeg</mime_type>
	  <transcode enabled="true">
	    <ext>mpg</ext>
	    <mime_type>video/mpeg</mime_type>
	    <transcoder>ffmpeg</transcoder>     
	    <video_codec>mpeg1video</video_codec>
	    <audio_codec>mp2</audio_codec>
	    <audio_samplerate>44100</audio_samplerate>             
	    <video_bitrate>1800000</video_bitrate>
	  </transcode>
	</file>
	<file ext="avi">
	  <type>VIDEO_ITEM_MOVIE</type>
	  <mime_type>video/x-msvideo</mime_type>
	  <transcode enabled="true">         
	    <transcoder>ffmpeg</transcoder>
	    <ext>mpg</ext>
	    <mime_type>video/mpeg</mime_type>         
	    <video_codec vcodec="mpeg4">mpeg2video</video_codec>
	    <audio_codec >mp2</audio_codec>	    
<video_bitrate>1800000</video_bitrate>
	    <audio_samplerate>44100</audio_samplerate>
	  </transcode>
	</file>
      </file_settings>
    </device>

I got video transcoding working but not audio... and other files work fully.:S

---

### Post by Egalfire on 2007-12-05
help please someone i keep getting this error when running the make command:

michael@michael-desktop:~/fuppes$ make
Making all in src
make[1]: Entering directory `/home/michael/fuppes/src'
if test -e "../version.sh"; then \
                ../version.sh; \
        fi
make  all-am
make[2]: Entering directory `/home/michael/fuppes/src'
/bin/bash ../libtool --tag=CXX   --mode=compile g++ -DHAVE_CONFIG_H -I. -I/usr/include/taglib -D__STDC_CONSTANT_MACROS -I/usr/include/ffmpeg    -I/usr/local/include -I/usr/include/ffmpeg   -I/usr/include/libxml2       -D_FILE_OFFSET_BITS=64    -g -O2   -MT UPnPAction.lo -MD -MP -MF .deps/UPnPAction.Tpo -c -o UPnPAction.lo `test -f 'lib/UPnPActions/UPnPAction.cpp' || echo './'`lib/UPnPActions/UPnPAction.cpp
 g++ -DHAVE_CONFIG_H -I. -I/usr/include/taglib -D__STDC_CONSTANT_MACROS -I/usr/include/ffmpeg -I/usr/local/include -I/usr/include/ffmpeg -I/usr/include/libxml2 -D_FILE_OFFSET_BITS=64 -g -O2 -MT UPnPAction.lo -MD -MP -MF .deps/UPnPAction.Tpo -c lib/UPnPActions/UPnPAction.cpp  -fPIC -DPIC -o .libs/UPnPAction.o
 g++ -DHAVE_CONFIG_H -I. -I/usr/include/taglib -D__STDC_CONSTANT_MACROS -I/usr/include/ffmpeg -I/usr/local/include -I/usr/include/ffmpeg -I/usr/include/libxml2 -D_FILE_OFFSET_BITS=64 -g -O2 -MT UPnPAction.lo -MD -MP -MF .deps/UPnPAction.Tpo -c lib/UPnPActions/UPnPAction.cpp -o UPnPAction.o >/dev/null 2>&1
mv -f .deps/UPnPAction.Tpo .deps/UPnPAction.Plo
/bin/bash ../libtool --tag=CXX   --mode=compile g++ -DHAVE_CONFIG_H -I. -I/usr/include/taglib -D__STDC_CONSTANT_MACROS -I/usr/include/ffmpeg    -I/usr/local/include -I/usr/include/ffmpeg   -I/usr/include/libxml2       -D_FILE_OFFSET_BITS=64    -g -O2   -MT FileDetails.lo -MD -MP -MF .deps/FileDetails.Tpo -c -o FileDetails.lo `test -f 'lib/ContentDirectory/FileDetails.cpp' || echo './'`lib/ContentDirectory/FileDetails.cpp
 g++ -DHAVE_CONFIG_H -I. -I/usr/include/taglib -D__STDC_CONSTANT_MACROS -I/usr/include/ffmpeg -I/usr/local/include -I/usr/include/ffmpeg -I/usr/include/libxml2 -D_FILE_OFFSET_BITS=64 -g -O2 -MT FileDetails.lo -MD -MP -MF .deps/FileDetails.Tpo -c lib/ContentDirectory/FileDetails.cpp  -fPIC -DPIC -o .libs/FileDetails.o
/usr/local/include/dlna.h:155: error: expected identifier before ';' token
/usr/local/include/dlna.h:155: error: multiple types in one declaration
/usr/local/include/dlna.h:155: error: declaration does not declare anything
/usr/include/ffmpeg/avcodec.h:2432: warning: attribute ignored in declaration of 'struct ImgReSampleContext'
/usr/include/ffmpeg/avcodec.h:2432: warning: attribute for 'struct ImgReSampleContext' must follow the 'struct' keyword
/usr/include/ffmpeg/avcodec.h:2437: warning: 'ImgReSampleContext' is deprecated (declared at /usr/include/ffmpeg/avcodec.h:2434)
/usr/include/ffmpeg/avcodec.h:2444: warning: 'ImgReSampleContext' is deprecated (declared at /usr/include/ffmpeg/avcodec.h:2434)
/usr/include/ffmpeg/avcodec.h:2448: warning: 'ImgReSampleContext' is deprecated (declared at /usr/include/ffmpeg/avcodec.h:2434)
/usr/include/ffmpeg/avcodec.h:2450: warning: 'ImgReSampleContext' is deprecated (declared at /usr/include/ffmpeg/avcodec.h:2434)
/usr/include/ffmpeg/avformat.h:282: warning: 'AVFrac' is deprecated (declared at /usr/include/ffmpeg/avformat.h:118)
lib/ContentDirectory/FileDetails.cpp: In member function 'std::string CFileDetails::GetDLNAString(std::string)':
lib/ContentDirectory/FileDetails.cpp:446: error: invalid conversion from 'int' to 'dlna_org_flags_t'
lib/ContentDirectory/FileDetails.cpp:448: error: 'dlna' was not declared in this scope
make[2]: *** [FileDetails.lo] Error 1
make[2]: Leaving directory `/home/michael/fuppes/src'
make[1]: *** [all] Error 2
make[1]: Leaving directory `/home/michael/fuppes/src'
make: *** [all-recursive] Error 1
michael@michael-desktop:~/fuppes$ 

thanx in advance

---

### Post by durand on 2007-12-05
Try the fuppes bug tracker.[http://sourceforge.net/tracker/?atid=751213&group_id=141999&func=browse](http://sourceforge.net/tracker/?atid=751213&group_id=141999&func=browse)

---

### Post by daodie on 2008-02-07
after i get to ./configure --enable-video-transcoding
i get these errors 
./configure: line 20137: PKG_PROG_PKG_CONFIG: command not found
./configure: line 20169: syntax error near unexpected token `PCRE,'
./configure: line 20169: `PKG_CHECK_MODULES(PCRE, libpcre >= 5.0)'

I'm using Ubuntu 7.10
Thanks :KS

*EDIT*
I figured it out
i installed pkg-config "apt-get install pkg-config"
then autoreconf -vfi
and ./configure worked!!

---

### Post by weazly on 2008-02-08
having trouble getting the files to show on the 360, v option didn't seem to help. I've been copying the configs posted on here with no luck. thanks for any help

---

### Post by terry_gardener on 2008-02-23
got this working with the ps3 video and audio both working. it took several hours to get right and working properly. 

here is my fuppes.cfg file for your reference/guide

<?xml version="1.0" encoding="UTF-8"?>
<fuppes_config version="0.7.2.3">
  <shared_objects>
    <dir>/home/terry/Videos</dir>
    <dir>/home/terry/Music</dir>
  </shared_objects>
  <network>
    <!--empty = automatic detection-->
    <interface>eth0</interface>
    <!--empty or 0 = random port-->
    <http_port>0</http_port>
    <!--list of ip addresses allowed to access fuppes. if empty all ips are allowed-->
    <allowed_ips>
      <!--<ip>192.168.0.1</ip>-->
      <ip>192.168.0.6</ip>
    </allowed_ips>
  </network>
  <content_directory>
    <!--a list of possible charsets can be found under:
      http://www.gnu.org/software/libiconv/-->
    <local_charset>UTF-8</local_charset>
    <!--libs used for metadata extraction when building the database. [true|false]-->
    <use_imagemagick>true</use_imagemagick>
    <use_taglib>true</use_taglib>
    <use_libavformat>true</use_libavformat>
  </content_directory>
  <transcoding>
    <!--[lame|twolame]-->
    <audio_encoder>lame</audio_encoder>
    <!--[true|false]-->
    <transcode_vorbis>true</transcode_vorbis>
    <transcode_musepack>true</transcode_musepack>
    <transcode_flac>true</transcode_flac>
  </transcoding>
  <device_settings>
    <!--"default" settings are inhertied by specific devices and can be overwritten-->
    <!--do NOT remove the "default" device settings-->
    <device name="default">
      <!--specify the maximum length for file names (0 or empty = unlimited)-->
      <max_file_name_length>0</max_file_name_length>
      <!--[file|container]-->
      <playlist_style>file</playlist_style>
      <show_childcount_in_title>false</show_childcount_in_title>
      <enable_dlna>false</enable_dlna>
      <transcoding_release_delay>4</transcoding_release_delay>
      <file_settings>
        <!--audio files-->
        <file ext="mp3">
          <type>AUDIO_ITEM</type>
          <mime_type>audio/mpeg</mime_type>
          <dlna>MP3</dlna>
        </file>
        <file ext="ogg">
          <type>AUDIO_ITEM</type>
          <mime_type>application/octet-stream</mime_type>
          <transcode enabled="true">
            <ext>mp3</ext>
            <mime_type>audio/mpeg</mime_type>
            <dlna>MP3</dlna>
            <http_encoding>chunked</http_encoding>
            <decoder>vorbis</decoder>
            <encoder>lame</encoder>
            <bitrate>192</bitrate>
            <samplerate>44100</samplerate>
          </transcode>
        </file>
        <file ext="mpc">
          <type>AUDIO_ITEM</type>
          <mime_type>application/octet-stream</mime_type>
          <transcode enabled="true">
            <ext>mp3</ext>
            <mime_type>audio/mpeg</mime_type>
            <dlna>MP3</dlna>
            <http_encoding>chunked</http_encoding>
            <decoder>musepack</decoder>
            <encoder>lame</encoder>
            <bitrate>192</bitrate>
            <samplerate>44100</samplerate>
          </transcode>
        </file>
        <file ext="wav">
          <type>AUDIO_ITEM</type>
          <mime_type>audio/x-wav</mime_type>
        </file>
        <file ext="flac">
          <type>AUDIO_ITEM</type>
          <mime_type>audio/x-flac</mime_type>
          <transcode enabled="true">
            <ext>mp3</ext>
            <mime_type>audio/mpeg</mime_type>
            <dlna>MP3</dlna>
            <http_encoding>chunked</http_encoding>
            <decoder>flac</decoder>
            <encoder>lame</encoder>
            <bitrate>192</bitrate>
            <samplerate>44100</samplerate>
          </transcode>
        </file>
        <file ext="wma">
          <type>AUDIO_ITEM</type>
          <mime_type>audio/x-ms-wma</mime_type>
          <dlna>WMAFULL</dlna>
        </file>
        <!--image files-->
        <file ext="jpg">
          <ext>jpeg</ext>
          <type>IMAGE_ITEM</type>
          <mime_type>image/jpeg</mime_type>
          <convert enabled="false">
            <!--<dcraw enabled="true">-q 0</dcraw>-->
            <ext>png</ext>
            <mime_type>image/png</mime_type>
            <height>0</height>
            <width>0</width>
            <!--set "greater" to "true" if you only want to resize images greater than "height" or "width"-->
            <greater>false</greater>
            <!--set "less" to "true" if you only want to resize images less than "height" or "width"-->
            <less>false</less>
            <!--set "less" and "greater" to "false" if you always want to resize-->
          </convert>
        </file>
        <file ext="bmp">
          <type>IMAGE_ITEM</type>
          <mime_type>image/bmp</mime_type>
        </file>
        <file ext="png">
          <type>IMAGE_ITEM</type>
          <mime_type>image/png</mime_type>
        </file>
        <file ext="gif">
          <type>IMAGE_ITEM</type>
          <mime_type>image/gif</mime_type>
        </file>
        <!--video files-->
        <file ext="mpg">
          <ext>mpeg</ext>
          <type>VIDEO_ITEM</type>
          <mime_type>video/mpeg</mime_type>
        </file>
        <file ext="mp4">
          <type>VIDEO_ITEM</type>
          <mime_type>video/mp4</mime_type>
        </file>
        <file ext="avi">
          <type>VIDEO_ITEM</type>
          <mime_type>video/x-msvideo</mime_type>
        </file>
        <file ext="wmv">
          <type>VIDEO_ITEM</type>
          <mime_type>video/x-ms-wmv</mime_type>
        </file>
        <file ext="vob">
          <type>VIDEO_ITEM</type>
          <mime_type>video/x-ms-vob</mime_type>
        </file>
        <file ext="vdr">
          <type>VIDEO_ITEM</type>
          <mime_type>video/x-extension-vdr</mime_type>
          <transcode enabled="true">
            <ext>vob</ext>
            <mime_type>video/x-ms-vob</mime_type>
          </transcode>
        </file>
        <file ext="flv">
          <type>VIDEO_ITEM</type>
          <mime_type>application/x-flash-video</mime_type>
        </file>
        <file ext="asf">
          <type>VIDEO_ITEM</type>
          <mime_type>video/x-ms-asf</mime_type>
        </file>
        <!--playlists-->
        <file ext="pls">
          <type>PLAYLIST</type>
          <mime_type>audio/x-scpls</mime_type>
        </file>
        <file ext="m3u">
          <type>PLAYLIST</type>
          <mime_type>audio/x-mpegurl</mime_type>
        </file>
      </file_settings>
    </device>
    <!--If you have more than one device it is a good idea to set the ip address manually as some devices may have conflicting "user agents".-->
    <!--It is safe to remove unneeded devices-->
    <device name="PS3" enabled="true">
      <user_agent>UPnP/1.0 DLNADOC/1.00</user_agent>
      <user_agent>PLAYSTATION3</user_agent>
      <!--<ip>192.168.0.6</ip>-->
      <enable_dlna>true</enable_dlna>
      <transcoding_release_delay>50</transcoding_release_delay>
      <file_settings>
        <file ext="ogg">
          <type>item.audioItem.musicTrack</type>
          <transcode enabled="true">
            <http_encoding>stream</http_encoding>
          </transcode>
        </file>
                <file ext="mpg">
          <type>VIDEO_ITEM</type>
          <transcode enabled="true">
            <transcoder>ffmpeg</transcoder>
            <mime_type>video/mpeg</mime_type>
            <ext>mpg</ext>
            <video_codec>copy</video_codec>
            <audio_codec>mp2</audio_codec>
            <audio_samplerate>44100</audio_samplerate>
            <audio_bitrate>192000</audio_bitrate>
          </transcode>
        </file>
        <file ext="avi">
          <type>VIDEO_ITEM</type>
          <mime_type>video/x-divx</mime_type>
          <transcode enabled="true">
            <transcoder>ffmpeg</transcoder>
            <ext>mpg</ext>
            <mime_type>video/mpeg</mime_type>
            <video_codec vcodec="msmpeg4">mpeg1video</video_codec>
            <video_bitrate>1800000</video_bitrate>
            <audio_codec acodec="wmav2">mp2</audio_codec>
            <audio_samplerate>44100</audio_samplerate>
            <audio_bitrate>192000</audio_bitrate>
          </transcode>
        </file>
        <file ext="mkv">
          <type>VIDEO_ITEM</type>
          <mime_type>video/x-matroska</mime_type>
          <transcode enabled="true">
            <transcoder>ffmpeg</transcoder>
            <ext>mpg</ext>
            <mime_type>video/mpeg</mime_type>
            <video_codec>mpeg2video</video_codec>
            <video_bitrate>1800000</video_bitrate>
            <audio_codec>mp2</audio_codec>
            <audio_samplerate>44100</audio_samplerate>
            <audio_bitrate>192000</audio_bitrate>
          </transcode>
        </file>
<file ext="avi">
          <type>VIDEO_ITEM</type>
          <mime_type>video/x-msvideo</mime_type>
          <transcode enabled="true">
            <transcoder>ffmpeg</transcoder>
            <ext>mpg</ext>
            <mime_type>video/mpeg</mime_type>
            <video_codec>mpeg2video</video_codec>
            <video_bitrate>1800000</video_bitrate>
            <audio_codec>mp2</audio_codec>
            <audio_samplerate>44100</audio_samplerate>
            <audio_bitrate>192000</audio_bitrate>
          </transcode>
        </file>
      </file_settings>
    </device>
    <device name="Xbox 360" virtual="Xbox 360" enabled="false">
      <user_agent>Xbox/2.0.\d+.\d+ UPnP/1.0 Xbox/2.0.\d+.\d+</user_agent>
      <user_agent>Xenon</user_agent>
      <xbox360>true</xbox360>
    </device>
    <device name="Noxon audio" virtual="default" enabled="false">
      <!--Please enter the address of your Noxon. Automatic detection is impossible because the Noxon does not send a "user-agent" in it's requests-->
      <!--<ip></ip>-->
      <playlist_style>container</playlist_style>
      <show_childcount_in_title>true</show_childcount_in_title>
    </device>
    <device name="Telegent TG 100" virtual="default" enabled="false">
      <user_agent>dma/1.0 \(http://www.cybertan.com.tw/\)</user_agent>
      <user_agent>UPnP/1.0 DLNADOC/1.00</user_agent>
      <playlist_style>file</playlist_style>
      <max_file_name_length>101</max_file_name_length>
    </device>
  </device_settings>
</fuppes_config>

---

### Post by durand on 2008-02-23
thanks! I need to try that config...All I need fuppes for now is ogg playback.

---

### Post by Spikextrem on 2008-02-24
Hi,

I tried the PS3 config posted earlier that I added my xbox config to it to see if this works for me. My server is seen by the xbox 360 but when it connects it says that there is no media available.


What is wrong?

<?xml version="1.0" encoding="UTF-8"?>
<fuppes_config version="0.7.2.3">
<shared_objects>
    <dir>/mnt/sda1/Share/Video/Movies</dir>
</shared_objects>
<network>
<!--empty = automatic detection-->
<interface>eth0</interface>
<!--empty or 0 = random port-->
<http_port>10001</http_port>
<!--list of ip addresses allowed to access fuppes. if empty all ips are allowed-->
<allowed_ips>
<!--<ip>192.168.0.1</ip>-->
</allowed_ips>
</network>
<content_directory>
<!--a list of possible charsets can be found under:
http://www.gnu.org/software/libiconv/-->
<local_charset>UTF-8</local_charset>
<!--libs used for metadata extraction when building the database. [true|false]-->
<use_imagemagick>true</use_imagemagick>
<use_taglib>true</use_taglib>
<use_libavformat>true</use_libavformat>
</content_directory>
<transcoding>
<!--[lame|twolame]-->
<audio_encoder>lame</audio_encoder>
<!--[true|false]-->
<transcode_vorbis>true</transcode_vorbis>
<transcode_musepack>true</transcode_musepack>
<transcode_flac>true</transcode_flac>
</transcoding>
<device_settings>
<!--"default" settings are inhertied by specific devices and can be overwritten-->
<!--do NOT remove the "default" device settings-->
<device name="default">
<!--specify the maximum length for file names (0 or empty = unlimited)-->
<max_file_name_length>0</max_file_name_length>
<!--[file|container]-->
<playlist_style>file</playlist_style>
<show_childcount_in_title>false</show_childcount_in_title>
<enable_dlna>false</enable_dlna>
<transcoding_release_delay>4</transcoding_release_delay>
<file_settings>
<!--audio files-->
<file ext="mp3">
<type>AUDIO_ITEM</type>
<mime_type>audio/mpeg</mime_type>
<dlna>MP3</dlna>
</file>
<file ext="ogg">
<type>AUDIO_ITEM</type>
<mime_type>application/octet-stream</mime_type>
<transcode enabled="true">
<ext>mp3</ext>
<mime_type>audio/mpeg</mime_type>
<dlna>MP3</dlna>
<http_encoding>chunked</http_encoding>
<decoder>vorbis</decoder>
<encoder>lame</encoder>
<bitrate>192</bitrate>
<samplerate>44100</samplerate>
</transcode>
</file>
<file ext="mpc">
<type>AUDIO_ITEM</type>
<mime_type>application/octet-stream</mime_type>
<transcode enabled="true">
<ext>mp3</ext>
<mime_type>audio/mpeg</mime_type>
<dlna>MP3</dlna>
<http_encoding>chunked</http_encoding>
<decoder>musepack</decoder>
<encoder>lame</encoder>
<bitrate>192</bitrate>
<samplerate>44100</samplerate>
</transcode>
</file>
<file ext="wav">
<type>AUDIO_ITEM</type>
<mime_type>audio/x-wav</mime_type>
</file>
<file ext="flac">
<type>AUDIO_ITEM</type>
<mime_type>audio/x-flac</mime_type>
<transcode enabled="true">
<ext>mp3</ext>
<mime_type>audio/mpeg</mime_type>
<dlna>MP3</dlna>
<http_encoding>chunked</http_encoding>
<decoder>flac</decoder>
<encoder>lame</encoder>
<bitrate>192</bitrate>
<samplerate>44100</samplerate>
</transcode>
</file>
<file ext="wma">
<type>AUDIO_ITEM</type>
<mime_type>audio/x-ms-wma</mime_type>
<dlna>WMAFULL</dlna>
</file>
<!--image files-->
<file ext="jpg">
<ext>jpeg</ext>
<type>IMAGE_ITEM</type>
<mime_type>image/jpeg</mime_type>
<convert enabled="false">
<!--<dcraw enabled="true">-q 0</dcraw>-->
<ext>png</ext>
<mime_type>image/png</mime_type>
<height>0</height>
<width>0</width>
<!--set "greater" to "true" if you only want to resize images greater than "height" or "width"-->
<greater>false</greater>
<!--set "less" to "true" if you only want to resize images less than "height" or "width"-->
<less>false</less>
<!--set "less" and "greater" to "false" if you always want to resize-->
</convert>
</file>
<file ext="bmp">
<type>IMAGE_ITEM</type>
<mime_type>image/bmp</mime_type>
</file>
<file ext="png">
<type>IMAGE_ITEM</type>
<mime_type>image/png</mime_type>
</file>
<file ext="gif">
<type>IMAGE_ITEM</type>
<mime_type>image/gif</mime_type>
</file>
<!--video files-->
<file ext="mpg">
<ext>mpeg</ext>
<type>VIDEO_ITEM</type>
<mime_type>video/mpeg</mime_type>
</file>
<file ext="mp4">
<type>VIDEO_ITEM</type>
<mime_type>video/mp4</mime_type>
</file>
<file ext="avi">
<type>VIDEO_ITEM</type>
<mime_type>video/x-msvideo</mime_type>
</file>
<file ext="wmv">
<type>VIDEO_ITEM</type>
<mime_type>video/x-ms-wmv</mime_type>
</file>
<file ext="vob">
<type>VIDEO_ITEM</type>
<mime_type>video/x-ms-vob</mime_type>
</file>
<file ext="vdr">
<type>VIDEO_ITEM</type>
<mime_type>video/x-extension-vdr</mime_type>
<transcode enabled="true">
<ext>vob</ext>
<mime_type>video/x-ms-vob</mime_type>
</transcode>
</file>
<file ext="flv">
<type>VIDEO_ITEM</type>
<mime_type>application/x-flash-video</mime_type>
</file>
<file ext="asf">
<type>VIDEO_ITEM</type>
<mime_type>video/x-ms-asf</mime_type>
</file>
<!--playlists-->
<file ext="pls">
<type>PLAYLIST</type>
<mime_type>audio/x-scpls</mime_type>
</file>
<file ext="m3u">
<type>PLAYLIST</type>
<mime_type>audio/x-mpegurl</mime_type>
</file>
</file_settings>
</device>


<!--If you have more than one device it is a good idea to set the ip address manually as some devices may have conflicting "user agents".-->
<!--It is safe to remove unneeded devices-->
<device name="PS3" enabled="false">
<user_agent>UPnP/1.0 DLNADOC/1.00</user_agent>
<user_agent>PLAYSTATION3</user_agent>
<!--<ip>192.168.0.6</ip>-->
<enable_dlna>true</enable_dlna>
<transcoding_release_delay>50</transcoding_release_delay>
<file_settings>
<file ext="ogg">
<type>item.audioItem.musicTrack</type>
<transcode enabled="true">
<http_encoding>stream</http_encoding>
</transcode>
</file>
<file ext="mpg">
<type>VIDEO_ITEM</type>
<transcode enabled="true">
<transcoder>ffmpeg</transcoder>
<mime_type>video/mpeg</mime_type>
<ext>mpg</ext>
<video_codec>copy</video_codec>
<audio_codec>mp2</audio_codec>
<audio_samplerate>44100</audio_samplerate>
<audio_bitrate>192000</audio_bitrate>
</transcode>
</file>
<file ext="avi">
<type>VIDEO_ITEM</type>
<mime_type>video/x-divx</mime_type>
<transcode enabled="true">
<transcoder>ffmpeg</transcoder>
<ext>mpg</ext>
<mime_type>video/mpeg</mime_type>
<video_codec vcodec="msmpeg4">mpeg1video</video_codec>
<video_bitrate>1800000</video_bitrate>
<audio_codec acodec="wmav2">mp2</audio_codec>
<audio_samplerate>44100</audio_samplerate>
<audio_bitrate>192000</audio_bitrate>
</transcode>
</file>
<file ext="mkv">
<type>VIDEO_ITEM</type>
<mime_type>video/x-matroska</mime_type>
<transcode enabled="true">
<transcoder>ffmpeg</transcoder>
<ext>mpg</ext>
<mime_type>video/mpeg</mime_type>
<video_codec>mpeg2video</video_codec>
<video_bitrate>1800000</video_bitrate>
<audio_codec>mp2</audio_codec>
<audio_samplerate>44100</audio_samplerate>
<audio_bitrate>192000</audio_bitrate>
</transcode>
</file>
<file ext="avi">
<type>VIDEO_ITEM</type>
<mime_type>video/x-msvideo</mime_type>
<transcode enabled="true">
<transcoder>ffmpeg</transcoder>
<ext>mpg</ext>
<mime_type>video/mpeg</mime_type>
<video_codec>mpeg2video</video_codec>
<video_bitrate>1800000</video_bitrate>
<audio_codec>mp2</audio_codec>
<audio_samplerate>44100</audio_samplerate>
<audio_bitrate>192000</audio_bitrate>
</transcode>
</file>
</file_settings>
</device>

<device name="Xbox 360" virtual="Xbox 360" enabled="true">
  <user_agent>Xbox/2.0.\d+.\d+ UPnP/1.0 Xbox/2.0.\d+.\d+</user_agent>
  <user_agent>Xenon</user_agent>
  <xbox360>true</xbox360>
  <show_empty_resolution>true</show_empty_resolution>
  <description_values>
    <friendly_name>%s %v : 1 : Windows Media Connect</friendly_name>
    <model_name>Windows Media Connect compatible (%s)</model_name>
    <model_number>2.0</model_number>
  </description_values>


  <file_settings>
    <file ext="mp3"><type>AUDIO_ITEM_MUSIC_TRACK</type></file>
    <file ext="jpg"><type>IMAGE_ITEM_PHOTO</type></file>
<file ext="wmv">
<type>VIDEO_ITEM</type>
<mime_type>video/x-ms-wmv</mime_type>
</file>


  </file_settings>
</device>


</device_settings>
</fuppes_config>


And if anyone has a working config file for a xbox360, please contact me or post it here, please.

---

### Post by ceecld on 2008-02-25
Hi i get the following errors when i run the make command. Any ideas what could be happening? 


```
chris@m1330-ubuntu:~/fuppes$ make
Making all in src
make[1]: Entering directory `/home/chris/fuppes/src'
if test -e "../version.sh"; then \
                ../version.sh; \
        fi
make  all-am
make[2]: Entering directory `/home/chris/fuppes/src'
make[2]: Leaving directory `/home/chris/fuppes/src'
make[1]: Leaving directory `/home/chris/fuppes/src'
Making all in src/gnome
make[1]: Entering directory `/home/chris/fuppes/src/gnome'
make[1]: Nothing to be done for `all'.
make[1]: Leaving directory `/home/chris/fuppes/src/gnome'
Making all in src/plugins
make[1]: Entering directory `/home/chris/fuppes/src/plugins'
/bin/bash ../../libtool --tag=CXX   --mode=compile g++ -DHAVE_CONFIG_H -I. -I../../src -D__STDC_CONSTANT_MACROS -I/usr/include/ffmpeg     -I/usr/include/libxml2         -g -O2 -MT metadata_taglib.lo -MD -MP -MF .deps/metadata_taglib.Tpo -c -o metadata_taglib.lo metadata_taglib.cpp
 g++ -DHAVE_CONFIG_H -I. -I../../src -D__STDC_CONSTANT_MACROS -I/usr/include/ffmpeg -I/usr/include/libxml2 -g -O2 -MT metadata_taglib.lo -MD -MP -MF .deps/metadata_taglib.Tpo -c metadata_taglib.cpp  -fPIC -DPIC -o .libs/metadata_taglib.o
metadata_taglib.cpp:3:21: error: fileref.h: No such file or directory
metadata_taglib.cpp:4:19: error: tfile.h: No such file or directory
metadata_taglib.cpp:5:17: error: tag.h: No such file or directory
metadata_taglib.cpp: In function 'int taglib_open_file(plugin_info*, char*)':
metadata_taglib.cpp:13: error: expected type-specifier before 'TagLib'
metadata_taglib.cpp:13: error: expected `;' before 'TagLib'
metadata_taglib.cpp:14: error: 'TagLib' has not been declared
metadata_taglib.cpp:14: error: expected primary-expression before ')' token
metadata_taglib.cpp:14: error: expected `)' before 'info'
metadata_taglib.cpp:19: error: expected `)' before '}' token
metadata_taglib.cpp:19: error: expected primary-expression before '}' token
metadata_taglib.cpp:19: error: expected `;' before '}' token
metadata_taglib.cpp: In function 'void taglib_get_title(plugin_info*)':
metadata_taglib.cpp:23: error: 'TagLib' has not been declared
metadata_taglib.cpp:23: error: expected `;' before 'sTmp'
metadata_taglib.cpp:25: error: 'sTmp' was not declared in this scope
metadata_taglib.cpp:25: error: 'TagLib' has not been declared
metadata_taglib.cpp:25: error: expected primary-expression before ')' token
metadata_taglib.cpp:25: error: expected `)' before 'info'
metadata_taglib.cpp: In function 'void taglib_get_duration(plugin_info*)':
metadata_taglib.cpp:31: error: 'TagLib' has not been declared
metadata_taglib.cpp:31: error: expected `;' before 'sTmp'
metadata_taglib.cpp:33: error: 'TagLib' has not been declared
metadata_taglib.cpp:33: error: expected primary-expression before ')' token
metadata_taglib.cpp:33: error: expected `)' before 'info'
make[1]: *** [metadata_taglib.lo] Error 1
make[1]: Leaving directory `/home/chris/fuppes/src/plugins'
make: *** [all-recursive] Error 1

```

---

### Post by terry_gardener on 2008-02-25
i kept getting error when trying to make the install using the instruction in the original post so i downloaded the source file from the fuppes website and then followed the instructions on the website. 

[http://fuppes.ulrich-voelkel.de/download/](http://fuppes.ulrich-voelkel.de/download/)

$ cd fuppes/
$ autoreconf -vfi
$ ./configure --enable-video-transcoding
$ make 
$ sudo make install
$ sudo ldconfig

then run the fuppes program to create the .fuppes directory and then edit the fuppes.cfg file. 

This is how i got it to work anyway. 

hope you get it fixed.

---

### Post by Alien18 on 2008-02-26
> **durand said:**
> Nice howto.

If anyone's interested, this is my PS3 config(taken from the wiki and modified:

***CONFIG FILE HERE***

I got video transcoding working but not audio... and other files work fully.:S

> **terry_gardener said:**
> got this working with the ps3 video and audio both working. it took several hours to get right and working properly. 

here is my fuppes.cfg file for your reference/guide
***CONFIG FILE HERE*** 

Hi All,

I'm new to Linux and trying to learn it's basics before building a media server.

I've tried both the configs above, I'm not at my Linux PC atm but, last night I was trying some different settings and options out.

So far I have had the most luck with durand's config file.

I'll stop waffling and get to the main problem, in the Video folder I'm using to test streaming I have 5 files 1 avi, 2 mp4 and 2 mkvs.  Using durand's config file I've successfully managed to stream the avi and mp4 files but the mkv (which I've added myself to the config file - in the same fashion as it's added to terry's) files aren't even been listed on my PS3, which is odd to say the least, I'd have a better idea of what to do if the files were showing up but as "Unsupported Data" but they're not being listed at all.

Has anyone successfully streamed mkv files to the PS3 with Fuppes?

If so I'd be very grateful if you could post your config file.

Many thanks,
Alien18

---

### Post by ceecld on 2008-02-26
Well i got it installed and my 360 is seeing the fuppes server, however i can't play AVI files through it. It gives me an error saying file type is not supported. Is this to do with the transcoding? 

FYI, im able to play the same avi files straight from vista with the WMP11 media server.

cheers

edit: cool, i got it i just disabled transcode. e.g.

```
<file ext="avi">
              <type>VIDEO_ITEM</type>
              <mime_type>video/x-msvideo</mime_type>
              <transcode enabled="false">         
                <transcoder>ffmpeg</transcoder>
                <ext>wmv</ext>
                <mime_type>video/x-ms-wmv</mime_type>         
                <video_codec>wmv2</video_codec>
                <audio_codec>wmav1</audio_codec>
                <video_bitrate>1800000</video_bitrate>
                <audio_bitrate>128000</audio_bitrate>
              </transcode>
            </file>
```

---

### Post by EnsignR on 2008-02-27
You shouldn't need to transcode avi files, the 360 is supposed to support them now (since the Fall Update). I do however have one avi in my library that still refuses to play.

If you use the mime_type video/avi the 360 SHOULD be able to play the AVIs using fuppes.

cheers

---

### Post by durand on 2008-02-27
> **Alien18 said:**
> Hi All,

I'm new to Linux and trying to learn it's basics before building a media server.

I've tried both the configs above, I'm not at my Linux PC atm but, last night I was trying some different settings and options out.

So far I have had the most luck with durand's config file.

I'll stop waffling and get to the main problem, in the Video folder I'm using to test streaming I have 5 files 1 avi, 2 mp4 and 2 mkvs.  Using durand's config file I've successfully managed to stream the avi and mp4 files but the mkv (which I've added myself to the config file - in the same fashion as it's added to terry's) files aren't even been listed on my PS3, which is odd to say the least, I'd have a better idea of what to do if the files were showing up but as "Unsupported Data" but they're not being listed at all.

Has anyone successfully streamed mkv files to the PS3 with Fuppes?

If so I'd be very grateful if you could post your config file.

Many thanks,
Alien18

Hmm.....I have a similar problem to you with my ogg music files...The ps3 used to show the ogg files even though they didnt work properly...but now, they are completely missed off the list... Weird..

Try posting a bug in the forums or bug tracker: [http://sourceforge.net/tracker/?atid=751213&group_id=141999&func=browse](http://sourceforge.net/tracker/?atid=751213&group_id=141999&func=browse)

---

### Post by azzinder on 2008-02-28
During the install I got the message:

/usr/bin/ld: cannot find -lungif
collect2: ld returned 1 exit status
make[2]: *** [libfuppes.la] Error 1
make[2]: Leaving directory `/home/nekten/fuppes/src'
make[1]: *** [all] Error 2
make[1]: Leaving directory `/home/nekten/fuppes/src'
make: *** [all-recursive] Error 1


Any ideas?

---

### Post by ghinch on 2008-03-13
Anyone know what settings I should be using for m4v and mov files? Also none of my music is showing up, does it matter that its contained within subdirectories of the shared music directory?

---

### Post by durand on 2008-03-13
it depends on the device. For PS3's, you need the music to be within a Music folder.

---

### Post by ghinch on 2008-03-14
oh sorry i'm trying to hook to an xbox 360. i think it must have something to do with my virtual folder setup, i copied my itunes.xml file from my computer and referenced that in the <itunes> tag, and now i can see all the albums, but only a few artists and none of my playlists. any ideas?

i also figured out m4v works if you just give them the video/mp4 mime type, still no luck with mov files.

---

### Post by durand on 2008-03-14
Hmm, your best bet is the bug tracker really...I don't use itunes and I'm not familiar enough with fuppes to help you. Sorry.

---

### Post by SumnerBoy on 2008-03-17
Hi - I have managed to get FUPPES running on my Ubuntu 7.10 Server streaming to my XBox 360. I can stream mp3s and flacs (the two formats my music is stored as) which is great - this is something I couldn't get working with Twonky.

I am also able to stream wmv and avi video but cannot stream mpg. Any ideas on how to configure FUPPES to stream mpg/mpeg? 

Also, I am not entirely happy with the structure when browsing. In the XBox 360 menus I select music and can then pick Artists or Albums. When selecting Artists I would then like to see a list of albums for that artist. I have turned on 'create_container_details=true' for the XBox 360 device vfolder.cfg but this didn't help.

When I access an artist it flashes up with 'No Albums Found' before listing all songs for that artist. All my metadata is correct and contains artist and album details.

Any ideas? I have read the vfolder.cfg help pages etc but it seems the XBox does things a little differently. I have the standard set of folder configurations but this seems to be ignored for the XBox as it has it's own menu structure.

I am a little lost!

---

### Post by vik.vaughn on 2008-03-20
Can this transcode 720p and 1080p .mkv files on the fly? That seems like a VERY processor intensive task. I know when I convert from one format to another on my PC, it usually can only muster about 2fps of encoding.

---

### Post by anotheraddict on 2008-03-24
Hey guys, just wondering if anyone could help point me in the right direction here.  I've followed this tutorial on getting Fuppes installed, and unfortunaly I'm getting stuck rather early on

```

dale@dale-desktop:~/fuppes$ sudo autoreconf -vfi
autoreconf: Entering directory `.'
autoreconf: configure.in: not using Gettext
autoreconf: running: aclocal --force 
configure.in:51: warning: macro `AM_ICONV' not found in library
autoreconf: configure.in: tracing
autoreconf: running: libtoolize --copy --force
configure.in:51: warning: macro `AM_ICONV' not found in library
autoreconf: running: /usr/bin/autoconf --force
configure.in:51: error: possibly undefined macro: AM_ICONV
      If this token and others are legitimate, please use m4_pattern_allow.
      See the Autoconf documentation.
autoreconf: /usr/bin/autoconf failed with exit status: 1
dale@dale-desktop:~/fuppes$ 

```

I've tried redoing steps 1 through 4 praying that It was something that I just overlooked, but try as I might, I cannot seem to resolve this.  Any help would be appreciated

also, before someone says it, I did attempt to find some documentation about the "use m4_pattern_allow" statement, but still I couldn't find anything that would lead me into the right direction

---

### Post by Ric_ on 2008-04-04
anotheraddict :- try doing

sudo apt-get install gettext

That fixed that problem for me.

---

### Post by mickfromperth on 2008-04-05
Hi just wanted to say thanks for this howto.  I now have streaming working to my PS3.  I'm playing with transcoding now and I'll post once I have transcoding to PS3 working.

---

### Post by Jaymo on 2008-04-09
I've managed to get it working for my ps3 but mkv transcoding is still hit and miss.
It chucks a fit about the audio stream, even with the -ac 2 ffmpeg parameter..
> [matroska @ 0xb793f110]Ignoring seekhead entry for ID=0x1549a966
[matroska @ 0xb793f110]Ignoring seekhead entry for ID=0x1654ae6b
[matroska @ 0xb793f110]Ignoring seekhead entry for ID=0x114d9b74
[matroska @ 0xb793f110]Unknown entry 0x73a4 in info header
[matroska @ 0xb793f110]Unknown track header entry 0x55aa - ignoring
[matroska @ 0xb793f110]Unknown track header entry 0x23314f - ignoring
[matroska @ 0xb793f110]Unknown track header entry 0x55ee - ignoring
[matroska @ 0xb793f110]Unknown track header entry 0xaa - ignoring
[matroska @ 0xb793f110]Unknown track header entry 0x55aa - ignoring
[matroska @ 0xb793f110]Unknown track header entry 0x23314f - ignoring
[matroska @ 0xb793f110]Unknown track header entry 0x55ee - ignoring
[matroska @ 0xb793f110]Unknown track header entry 0xaa - ignoring
Input #0, matroska, from '/media/sg750/Documentaries/planet.earth.part01.720p.hddvd.x264-medieval.mkv':
  Duration: 00:51:10.0, bitrate: N/A
  Stream #0.0: Audio: 0x0000, 48000 Hz, 5:1
  Stream #0.1: Video: h264, yuv420p, 1280x720, 23.98 fps(r)
Could not open '/tmp/fuppes/0.mpg'
Output #0, mpeg, to '/tmp/fuppes/0.mpg':
  Stream #0.0: Video: mpeg2video, yuv420p, 1280x720, q=2-31, 200 kb/s, 23.98 fps(c)
  Stream #0.1: Audio: mp2, 48000 Hz, stereo, 128 kb/s
Stream mapping:
  Stream #0.1 -> #0.0
  Stream #0.0 -> #0.1
Unsupported codec (id=86020) for input stream #0.0
== lib/Transcoding/TranscodingCache.cpp (562) :: Thu Apr 10 01:35:14 2008 ==
release object "/media/sg750/Documentaries/planet.earth.part01.720p.hddvd.x264-medieval.mkv"
ref count: 1
delay: 50


My MKV section says:
>         <file ext="mkv">
          <type>VIDEO_ITEM</type>
          <mime_type>video/x-matroska</mime_type>
          <transcode enabled="true">
            <transcoder>ffmpeg</transcoder>
            <ext>mpg</ext>
            <mime_type>video/mpeg</mime_type>
            <video_codec>mpeg2video</video_codec>
            <audio_codec>mp2</audio_codec>
            <ffmpeg_params>-ac 2</ffmpeg_params>
            <audio_bitrate>128000</audio_bitrate>
          </transcode>
        </file>


---

### Post by bear garden on 2008-04-13
> **Ric_ said:**
> anotheraddict :- try doing

sudo apt-get install gettext

That fixed that problem for me.

worked for me as well.

---

### Post by nhasian on 2008-05-07
I dont know if this will help or not, but the latest version of Fuppes is 611 and it is located at [https://fuppes.svn.sourceforge.net/svnroot/fuppes/]("https://fuppes.svn.sourceforge.net/svnroot/fuppes/")

---

### Post by SumnerBoy on 2008-05-07
Hi - I am newish to Linux but definitely not new to software development. I was hoping someone might take the time to point me in the right direction for help on compiling something like that latest version of FUPPES on Linux...?

---

### Post by nhasian on 2008-05-07
the step by step instructions are in the first post.  those are the instructions i used to install it.  the only difference is the location of the sourcecode has changed.  so use the instructions in the first post but replace:

> svn co [http://fuppes-svn.ulrich-voelkel.de/trunk](http://fuppes-svn.ulrich-voelkel.de/trunk) fuppes

with the newer version of the sourcecode here:

> svn co [https://fuppes.svn.sourceforge.net/svnroot/fuppes/trunk](https://fuppes.svn.sourceforge.net/svnroot/fuppes/trunk) fuppes

---

### Post by Doby on 2008-05-08
Bump

---

### Post by Doby on 2008-05-08
bump

---

### Post by Doby on 2008-05-08
These are my files

fuppes.cfg
--------------------------------------------------------------------------------------------------------------------------
<?xml version="1.0" encoding="UTF-8"?>
<fuppes_config version="0.7.2.3">
  <shared_objects>
    <!--<dir>/mnt/music</dir>-->
    <!--<itunes>/Users/.../iTunes.xml</itunes>-->
    <dir>/media/Free Agent/Downloads/Complete</dir>-->
  </shared_objects>
  <network>
    <!--empty = automatic detection-->
    <interface>eth0</interface>
    <!--empty or 0 = random port-->
    <http_port>9452</http_port>
    <!--list of ip addresses allowed to access fuppes. if empty all ips are allowed-->
    <allowed_ips>
      <!--<ip>192.168.0.1</ip>-->
      <ip>192.168.0.75</ip>
    </allowed_ips>
  </network>
  <content_directory>
    <!--a list of possible charsets can be found under:
      http://www.gnu.org/software/libiconv/-->
    <local_charset>UTF-8</local_charset>
    <!--libs used for metadata extraction when building the database. [true|false]-->
    <use_imagemagick>true</use_imagemagick>
    <use_taglib>true</use_taglib>
    <use_libavformat>true</use_libavformat>
  </content_directory>
 
<global_settings>
    <temp_dir/>
    <!--uuid is written to and read from <config-dir>/uuid.txt if set to true-->
    <use_fixed_uuid>false</use_fixed_uuid>
  </global_settings>
  <device_settings>
    <!--"default" settings are inhertied by specific devices and can be overwritten-->
    <!--do NOT remove the "default" device settings-->
    <!--all new file types have to be added to the default settings-->
    <!--adding new file types just to a specific device will have no affect-->
    <device name="Xbox 360" virtual="Xbox 360" enabled="true">
      <description_values>
        <friendly_name>%s %v : 1 : Windows Media Connect</friendly_name>
        <model_name>Windows Media Connect compatible (%s)</model_name>
        <model_number>2.0</model_number>
      </description_values>
      <user_agent>Xbox/2.0.\d+.\d+ UPnP/1.0 Xbox/2.0.\d+.\d+</user_agent>
      <user_agent>Xenon</user_agent>
      <xbox360>true</xbox360>
      <file_settings>
        <file ext="mp3">
          <type>AUDIO_ITEM_MUSIC_TRACK</type>
        </file>
        <file ext="jpg">
          <type>IMAGE_ITEM_PHOTO</type>
        </file>
        <file ext="avi">
          <type>VIDEO_ITEM</type>
          <mime_type>video/x-msvideo</mime_type>
          <transcode enabled="true">
            <transcoder>ffmpeg</transcoder>
            <ext>wmv</ext>
            <mime_type>video/x-ms-wmv</mime_type>
            <video_codec>wmv2</video_codec>
            <audio_codec>wmav1</audio_codec>
            <video_bitrate>1800000</video_bitrate>
            <audio_bitrate>128000</audio_bitrate>
          </transcode>
        </file>
      </file_settings>
    </device>
    <!--For other device settings take a look at http://fuppes.ulrich-voelkel.de/wiki/index.php/Category:Device-->
    <!--If you have more than one device it is a good idea to set the ip address as some devices may have conflicting "user agents".-->
    <!--It is safe to remove unneeded devices-->
    <device name="PS3" enabled="false">
      <user_agent>UPnP/1.0 DLNADOC/1.00</user_agent>
      <user_agent>PLAYSTATION3</user_agent>
      <!--<ip></ip>-->
      <enable_dlna>true</enable_dlna>
      <transcoding_release_delay>50</transcoding_release_delay>
      <file_settings>
        <file ext="ogg">
          <type>AUDIO_ITEM_MUSIC_TRACK</type>
          <transcode enabled="true">
            <http_encoding>stream</http_encoding>
          </transcode>
        </file>
      </file_settings>
    </device>
    <device name="Xbox 360" virtual="Xbox 360" enabled="false">
      <user_agent>Xbox/2.0.\d+.\d+ UPnP/1.0 Xbox/2.0.\d+.\d+</user_agent>
      <user_agent>Xenon</user_agent>
      <xbox360>true</xbox360>
      <show_empty_resolution>true</show_empty_resolution>
      <description_values>
        <friendly_name>%s %v : 1 : Windows Media Connect</friendly_name>
        <model_name>Windows Media Connect compatible (%s)</model_name>
        <model_number>2.0</model_number>
      </description_values>
    </device>
  </device_settings>
</fuppes_config>

vfolder.cfg
------------------------------------------------------------------------------------------------------------------------<?xml version="1.0" encoding="UTF-8"?> 
<fuppes_vfolder_config version="0.2"> 

 <vfolder_layout device="default" enabled="false"> 

    <vfolder name="Genre"> 
      <vfolders property="genre"> 
        <items type="audioItem" /> 
      </vfolders> 
    </vfolder> 

    <vfolder name="Genre/Artists"> 
      <vfolders property="genre"> 
        <vfolders property="artist"> 
          <items type="audioItem" /> 
        </vfolders> 
      </vfolders> 
    </vfolder> 

    <vfolder name="Artists/Albums"> 
      <vfolders property="artist"> 
        <vfolders property="album"> 
          <items type="audioItem" /> 
        </vfolders> 
      </vfolders> 
    </vfolder> 
    
    <vfolder name="ABC/Artists/Albums"> 
      <vfolders split="ABC"> 
        <vfolders property="artist"> 
          <vfolders property="album"> 
            <items type="audioItem" /> 
          </vfolders> 
        </vfolders> 
      </vfolders> 
    </vfolder> 
       
    <vfolder name="Photos"> 
      <vfolder name="All"> 
        <items type="imageItem" /> 
      </vfolder> 
      <vfolder name="Folders"> 
        <folders filter="contains(imageItem)" /> 
      </vfolder>      
    </vfolder> 

    <vfolder name="Videos"> 
      <vfolder name="All"> 
        <items type="videoItem" /> 
      </vfolder> 
      <vfolder name="Folders"> 
        <folders filter="contains(videoItem)" /> 
      </vfolder> 
    </vfolder> 
    
    <vfolder name="shared dirs"> 
      <shared_dirs full_extend="true" /> 
    </vfolder> 
    
  </vfolder_layout> 

  <vfolder_layout device="Xbox 360" enabled="true"> 

    <vfolder name="Music" id="1"> 
      <vfolder name="Album" id="7"> 
        <vfolders property="album" type="container.album.musicAlbum"> 
          <items type="audioItem" /> 
        </vfolders> 
      </vfolder> 
            
      <vfolder name="All Music" id="4"> 
        <items type="audioItem" /> 
      </vfolder> 
      
      <vfolder name="Artist" id="6"> 
        <vfolders property="artist" type="container.person.musicArtist"> 
          <items type="audioItem" /> 
        </vfolders> 
      </vfolder> 
      
      <vfolder name="Folders" id="20"> 
        <folders filter="contains(audioItem)" /> 
      </vfolder> 
      
      <vfolder name="Genre" id="5"> 
        <vfolders property="genre" type="container.genre.musicGenre"> 
          <items type="audioItem" /> 
        </vfolders> 
      </vfolder> 
      
      <vfolder name="Playlist" id="15" /> 
    </vfolder> 
   
    <vfolder name="Pictures" id="3"> 
      <vfolder name="Album" id="13" /> 
      
      <vfolder name="All Pictures" id="11"> 
        <items type="imageItem" /> 
      </vfolder> 
      
      <vfolder name="Date Taken" id="12" /> 
      
      <vfolder name="Folders" id="22"> 
        <folders filter="contains(imageItem)" /> 
      </vfolder> 
    </vfolder> 

    <vfolder name="Playlists" id="18"> 
      <vfolder name="All Playlists" id="19" /> 
      <vfolder name="Folders" id="23" /> 
    </vfolder> 

    <vfolder name="Video" id="2"> 
      <vfolder name="Actor" id="10"> 
        <folders filter="contains(videoItem)" /> 
      </vfolder> 
      <vfolder name="Album" id="14" /> 
      <vfolder name="All Video" id="8"> 
				<items type="videoItem" /> 
			</vfolder> 
      <vfolder name="Folders" id="21"> 
			   <folders filter="contains(videoItem)" /> 
      </vfolder> 
      <vfolder name="Genre" id="9" /> 
    </vfolder> 

  </vfolder_layout> 

</fuppes_vfolder_config>
--------------------------------------------------------------------------------------------------------------------------

And this is what i get 

tobin@Ubuntu:~/fuppes$ fuppes
            FUPPES - 0.611
    the Free UPnP Entertainment Service
      [http://fuppes.ulrich-voelkel.de](http://fuppes.ulrich-voelkel.de)

== lib/Plugins/Plugin.cpp (107) :: Thu May  8 23:40:29 2008 ==
registered metadata plugin "libavformat"

== lib/Plugins/Plugin.cpp (121) :: Thu May  8 23:40:29 2008 ==
registered transcoder plugin "ffmpeg"

webinterface: [http://192.168.0.75:9452](http://192.168.0.75:9452)

r = rebuild database
u = update database
i = print system info
h = print help

press "ctrl-c" or "q" to quit

:1: parser warning : xmlns:ms: ' urn:microsoft-com:wmc-1-0' is not a valid URI
ot xmlns="urn:schemas-upnp-org:device-1-0" xmlns:ms=" urn:microsoft-com:wmc-1-0"
                                                                               ^
== lib/Fuppes.cpp (346) :: Thu May  8 23:40:30 2008 ==
new device: Xbox 360 :: MediaRenderer

new UPnP device:
Xbox 360 (MediaRenderer)
r
[ContentDatabase] create database at Thu May  8 23:40:38 2008
read shared directories
[DONE] read shared directories
parse playlists
[DONE] parse playlists
parse iTunes databases
[DONE] parse iTunes databases
[ContentDatabase] database created at Thu May  8 23:41:03 2008
v
[VirtualContainer] create virtual container layout started at Thu May  8 23:46:36 2008
[VirtualContainer] virtual container layout created at Thu May  8 23:46:37 2008


but my 360 does not see my computer

---

### Post by kingbin on 2008-05-09
I've only had a chance to mess around a bit with the config. I was wondering if anyone has had any luck transcoding a VOB? I was wondering too if anyone has a working config of the max resolution you can stream to the xbox.

Thanks in advance

---

### Post by durand on 2008-05-09
I guess you could check if your firewall is blocking it?

---

### Post by PorchSong on 2008-05-09
Got fuppes up and working no problems.  But I have never been able to find out how to set up folders properly so that they all do not dump in one folder on Xbox 360.  Is there a how-to to setting up virtual folders or folder tree in fuppes so I don't have to surf through a ton of items?  This is especially frustrating when some of the vid names are 01, 02, 15, etc.  Or when you have a season of a tv series scattered all over as they are not uniformly named.

---

### Post by S0VERE1GN on 2008-05-10
why can't i get my fuppes to install? i get stuck here: 
cd fuppes/
$ autoreconf -vfi
$ ./configure --enable-video-transcoding
$ make
$ sudo make install
$ sudo ldconfig
 i just pasted it into the terminal just like that..whats the newb mistake im making? :lolflag:

---

### Post by S0VERE1GN on 2008-05-10
i added the URL line before that as well, but it seems liek nothing happens...what's going on?
.........

---

### Post by Horn on 2008-05-14
> **PorchSong said:**
> I got caught in same loop.  Do this: (I like to run these individually rather than all at once to watch what is going on).

$ sudo apt-get remove autoconf
$ sudo apt-get remove automake
$ sudo apt-get remove gettext

Go to your /home/**your user name**/ directory and delete your /fuppes directory if you see it in there.  NOT the hidden .fuppes directory as this only contains your fuppes.cfg and vfolder.cfg files. (no need to).  

So, now you are "clean."

Now start over.  

$ sudo apt-get update

$ sudo apt-get install autoconf
$ sudo apt-get install automake
$ sudo apt-get install gettext

Now get the latest release of fuppes v611 (Again, I run these one line at a time)

$ svn co [https://fuppes.svn.sourceforge.net/svnroot/fuppes/trunk](https://fuppes.svn.sourceforge.net/svnroot/fuppes/trunk) fuppes
$ cd fuppes
$ autoreconf -vfi
$ ./configure --enable-video-transcoding
$ make
$ sudo make install
$ sudo ldconfig


I've followed these steps but I'm getting an error make.  It looks like it can't find avformat.h but I have it on my system in the following locations:
```

/usr/include/ffmpeg/avformat.h
/usr/local/include/libavformat/avformat.h

```

I'm at a loss here since it looks like it should be working.  Any ideas guys?

Here's the make output
```
Making all in src
make[1]: Entering directory `/home/horn/fuppes/src'
make  all-am
make[2]: Entering directory `/home/horn/fuppes/src'
make[2]: Nothing to be done for `all-am'.
make[2]: Leaving directory `/home/horn/fuppes/src'
make[1]: Leaving directory `/home/horn/fuppes/src'
Making all in src/plugins
make[1]: Entering directory `/home/horn/fuppes/src/plugins'
/bin/bash ../../libtool --tag=CC   --mode=compile gcc -DHAVE_CONFIG_H -I. -I../../src    -I/usr/local/include   -g -O2 -MT libmetadata_libavformat_la-metadata_libavformat.lo -MD -MP -MF .deps/libmetadata_libavformat_la-metadata_libavformat.Tpo -c -o libmetadata_libavformat_la-metadata_libavformat.lo `test -f 'metadata_libavformat.c' || echo './'`metadata_libavformat.c
 gcc -DHAVE_CONFIG_H -I. -I../../src -I/usr/local/include -g -O2 -MT libmetadata_libavformat_la-metadata_libavformat.lo -MD -MP -MF .deps/libmetadata_libavformat_la-metadata_libavformat.Tpo -c metadata_libavformat.c  -fPIC -DPIC -o .libs/libmetadata_libavformat_la-metadata_libavformat.o
metadata_libavformat.c:31:22: error: avformat.h: No such file or directory
metadata_libavformat.c:32:21: error: avcodec.h: No such file or directory
metadata_libavformat.c: In function âfuppes_metadata_file_openâ:
metadata_libavformat.c:51: error: âAVFormatContextâ undeclared (first use in this function)
metadata_libavformat.c:51: error: (Each undeclared identifier is reported only once
metadata_libavformat.c:51: error: for each function it appears in.)
metadata_libavformat.c:51: error: expected expression before â)â token
metadata_libavformat.c:52: error: expected expression before â)â token
metadata_libavformat.c: In function âfuppes_metadata_readâ:
metadata_libavformat.c:62: error: âAVFormatContextâ undeclared (first use in this function)
metadata_libavformat.c:62: error: expected expression before â)â token
metadata_libavformat.c:62: error: âAV_NOPTS_VALUEâ undeclared (first use in this function)
metadata_libavformat.c:65: error: expected expression before â)â token
metadata_libavformat.c:65: error: âAV_TIME_BASEâ undeclared (first use in this function)
metadata_libavformat.c:66: error: expected expression before â)â token
metadata_libavformat.c:80: error: expected expression before â)â token
metadata_libavformat.c:81: error: expected expression before â)â token
metadata_libavformat.c:89: error: expected expression before â)â token
metadata_libavformat.c:91: error: âAVStreamâ undeclared (first use in this function)
metadata_libavformat.c:91: error: âpStreamâ undeclared (first use in this function)
metadata_libavformat.c:91: error: expected expression before â)â token
metadata_libavformat.c:92: error: âAVCodecâ undeclared (first use in this function)
metadata_libavformat.c:92: error: âpCodecâ undeclared (first use in this function)
metadata_libavformat.c:136: error: âCODEC_TYPE_VIDEOâ undeclared (first use in this function)
metadata_libavformat.c:142: error: âCODEC_TYPE_AUDIOâ undeclared (first use in this function)
metadata_libavformat.c:148: error: âCODEC_TYPE_DATAâ undeclared (first use in this function)
metadata_libavformat.c:150: error: âCODEC_TYPE_SUBTITLEâ undeclared (first use in this function)
make[1]: *** [libmetadata_libavformat_la-metadata_libavformat.lo] Error 1
make[1]: Leaving directory `/home/horn/fuppes/src/plugins'
make: *** [all-recursive] Error 1

```

---

### Post by stewils on 2008-05-15
I'm just about to give up.....
I've followed this tutorial and the one on the fuppes wiki and still got numerous missing dependencies, downloaded some of them from their websites, tar'd them, made them, made installed them, moved onto the next one, but, despite the fact that I've just done this for sqlite-amalgamation-3.5.9.tar.gz fuppes still won't configure and says:

 	  ```
checking for SQLITE3... configure: error: Package requirements (sqlite3 >= 3.2) were not met:

No package 'sqlite3' found

Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix.

Alternatively, you may set the environment variables SQLITE3_CFLAGS
and SQLITE3_LIBS to avoid the need to call pkg-config.
See the pkg-config man page for more details.
```

PLease, please, some one help....

---

### Post by durand on 2008-05-15
sudo aptitude install libsqlite3-dev

---

### Post by stewils on 2008-05-15
thanks.  Gave it a try but get the same error.. :(

---

### Post by durand on 2008-05-16
Thats strange...What version of ubuntu are you using?

---

### Post by nhasian on 2008-05-17
I'm using Fuppes 0611 with both my xbox360 and my PS3.  It works fine but I must admit it was rather cumbersome to configure the fuppes.config file.  Plus I still dont have it working with MKV files.  Its such a great program, I'm sure a lot more people would use it if it came with sample .config files for different systems, or if there was an html file you could launch to allow create your own fuppes.config file by ticking checkboxes for enabling or disabling transcoding for different filetypes, or to enable or disable xbox360 or PS3 support etc.

---

### Post by stewils on 2008-05-18
> **durand said:**
> Thats strange...What version of ubuntu are you using?
Latest update, Hardy Heron 8.04

---

### Post by PorchSong on 2008-05-21
> **nhasian said:**
> I'm using Fuppes 0611 with both my xbox360 and my PS3.  It works fine but I must admit it was rather cumbersome to configure the fuppes.config file.  Plus I still dont have it working with MKV files.  Its such a great program, I'm sure a lot more people would use it if it came with sample .config files for different systems, or if there was an html file you could launch to allow create your own fuppes.config file by ticking checkboxes for enabling or disabling transcoding for different filetypes, or to enable or disable xbox360 or PS3 support etc.

You won't get .mkv files to stream.  Xbox 360 nor PS3 will play them.  You have to convert to .avi / xvid first.  Also, fuppes does not transcode .mkv's.  So, the hd stuff has to be manually converted.  Pain in the *** if you ask me, but such is life.

---

### Post by FlypSyde on 2008-06-30
@Horn

> make[1]: *** [libmetadata_libavformat_la-metadata_libavformat.lo] Error 1
make[1]: Leaving directory `/home/horn/fuppes/src/plugins'
make: *** [all-recursive] Error 1

Did you ever figure this error out? I'm getting the same thing. I had fuppes 611 running without video transcoding (was able to view pics and play audio on my PS3). I then installed ffmpeg from source (SVN r14031) and when I went back to recompile fuppes to enable video transcoding and I get the error above during make whether I enable video transcoding or not. I am running the server edition of Gutsy.

Anyone???

---

### Post by FlypSyde on 2008-06-30
I now have ffmpeg svn14040 installed and running (or seeming to anyway, ffmpeg -version responds correctly) and fuppes 611 installed and running, but no video transcoding. If I try to run:

 ./configure --enable-video-transcoding

I get the following errors:

----------
[SIZE="1"]Making all in src/plugins
make[1]: Entering directory `/home/elvis/fuppes/src/plugins'
/bin/bash ../../libtool --tag=CC   --mode=compile gcc -DHAVE_CONFIG_H -I. -I../../src    -I/usr/local/include   -g -O2 -MT libmetadata_libavformat_la-metadata_libavformat.lo -MD -MP -MF .deps/libmetadata_libavformat_la-metadata_libavformat.Tpo -c -o libmetadata_libavformat_la-metadata_libavformat.lo `test -f 'metadata_libavformat.c' || echo './'`metadata_libavformat.c
mkdir .libs
 gcc -DHAVE_CONFIG_H -I. -I../../src -I/usr/local/include -g -O2 -MT libmetadata_libavformat_la-metadata_libavformat.lo -MD -MP -MF .deps/libmetadata_libavformat_la-metadata_libavformat.Tpo -c metadata_libavformat.c  -fPIC -DPIC -o .libs/libmetadata_libavformat_la-metadata_libavformat.o
metadata_libavformat.c:31:22: error: avformat.h: No such file or directory
metadata_libavformat.c:32:21: error: avcodec.h: No such file or directory
metadata_libavformat.c: In function 'fuppes_metadata_file_open':
metadata_libavformat.c:51: error: 'AVFormatContext' undeclared (first use in this function)
metadata_libavformat.c:51: error: (Each undeclared identifier is reported only once
metadata_libavformat.c:51: error: for each function it appears in.)
metadata_libavformat.c:51: error: expected expression before ')' token
metadata_libavformat.c:52: error: expected expression before ')' token
metadata_libavformat.c: In function 'fuppes_metadata_read':
metadata_libavformat.c:62: error: 'AVFormatContext' undeclared (first use in this function)
metadata_libavformat.c:62: error: expected expression before ')' token
metadata_libavformat.c:62: error: 'AV_NOPTS_VALUE' undeclared (first use in this function)
metadata_libavformat.c:65: error: expected expression before ')' token
metadata_libavformat.c:65: error: 'AV_TIME_BASE' undeclared (first use in this function)
metadata_libavformat.c:66: error: expected expression before ')' token
metadata_libavformat.c:80: error: expected expression before ')' token
metadata_libavformat.c:81: error: expected expression before ')' token
metadata_libavformat.c:89: error: expected expression before ')' token
metadata_libavformat.c:91: error: 'AVStream' undeclared (first use in this function)
metadata_libavformat.c:91: error: 'pStream' undeclared (first use in this function)
metadata_libavformat.c:91: error: expected expression before ')' token
metadata_libavformat.c:92: error: 'AVCodec' undeclared (first use in this function)
metadata_libavformat.c:92: error: 'pCodec' undeclared (first use in this function)
metadata_libavformat.c:136: error: 'CODEC_TYPE_VIDEO' undeclared (first use in this function)
metadata_libavformat.c:142: error: 'CODEC_TYPE_AUDIO' undeclared (first use in this function)
metadata_libavformat.c:148: error: 'CODEC_TYPE_DATA' undeclared (first use in this function)
metadata_libavformat.c:150: error: 'CODEC_TYPE_SUBTITLE' undeclared (first use in this function)
make[1]: *** [libmetadata_libavformat_la-metadata_libavformat.lo] Error 1
make[1]: Leaving directory `/home/elvis/fuppes/src/plugins'
make: *** [all-recursive] Error 1[/SIZE]
----------

If I run:

./configure --disable-libavformat

Which is supposed to disable use of libavformat from the ffmpeg package, fuppes compiles and installs with no errors and I can use fuppes to view pics and play music from my PS3.

Is this a fuppes problem or a ffmpeg problem? I'm running Ubuntu 7.10 server edition with ffmpeg 14040 and fuppes 611.

Some help would be greatly appreciated! :)

---

### Post by FlypSyde on 2008-07-01
I tried this same install of ffmpeg and fuppes with Hardy and I'm getting s similar error during make of fuppes. ffmpeg compiled and installed with no problems but fuppes errors during make with libavformat enabled. If I disable libavformat fuppes works fine with my PS3, but only for audio and pics.

I have a couple questions if anyone can answer them.

1. I understand that ffmpeg is necessary for fuppes to do on-the-fly transcoding, but is it still required if the video files are already in a format supported by the client device? (PS3 in my case)

2. Has anyone got ffmpeg and fuppes 100% working on either Gutsy or Hardy? If so, what versions of ffmpeg, fuppes, and Ubuntu are you running?

Constructive replies would be appreciated :-)

---

### Post by FlypSyde on 2008-07-05
I've given up on this and gone over to mediatomb. Got that up and running in a few hours.

---

### Post by WorldOfHurt on 2008-07-10
You have not installed the ...-dev packages for ffmpeg and its dependencies.  That's why you don't have the required header (.h) files, but the ffmpeg program works ok.

You need dev versions of all the fuppes dependencies before you can compile it.

---

### Post by BrokenKingpin on 2008-07-15
Everything is working (on my xbox 360) except I have to view my music by the "Songs" menu. Does anyone know how to get it so that the artists and albums show up properly on the 360?

---

### Post by BrokenKingpin on 2008-07-16
Anyone?

---

### Post by jcr1 on 2008-07-20
Hi...I cannot get this to install properly.

I run thru all the instructions and no errors are thrown up. After ldconfig, nothing happens.

There is no .fuppes directory, there is no .cfg to open...

Whats going wrong?

---

### Post by BrokenKingpin on 2008-07-21
jcr1, I have to actually run Fuppes before the .fuppes folder appeared. Just run Fuppes from the command (just type fuppes and hit enter). Run the r and v commands and then quite fuppes. The .fuppes folder should not appear.

Now can anyone tell me how to get the artist and albums to show up properly on the 360?

---

### Post by wasutton3 on 2008-07-22
i have it installed properly i think, when i start fuppes i get the following. im trying to get this to work with my ps3 and i know i had it working before on a testing rig, i just cant remember how i did it now:mad:

> serverbox@serverbox:~/.fuppes$ fuppes
            FUPPES - 0.614
    the Free UPnP Entertainment Service
      [http://fuppes.ulrich-voelkel.de](http://fuppes.ulrich-voelkel.de)

/home/serverbox/.fuppes/fuppes.cfg:14: parser error : Opening and ending tag mismatch: http_port line 9 and network
  </network>
            ^
/home/serverbox/.fuppes/fuppes.cfg:209: parser error : Opening and ending tag mismatch: interface line 7 and fuppes_config
</fuppes_config>
                ^
/home/serverbox/.fuppes/fuppes.cfg:210: parser error : Premature end of data in tag network line 5

^
/home/serverbox/.fuppes/fuppes.cfg:210: parser error : Premature end of data in tag fuppes_config line 2

^
== lib/SharedConfig.cpp (423) :: Tue Jul 22 10:42:50 2008 ==
parse error

my fuppes.cfg reads

> <?xml version="1.0" encoding="UTF-8"?>
<fuppes_config version="0.7.2.3">
  <shared_objects>
  </shared_objects>
  <network>
    <!--empty = automatic detection-->
   <interface>eth0<interface/>
    <!--empty or 0 = random port-->
    <http_port>8080<http_port/>
    <!--list of ip addresses allowed to access fuppes. if empty all ips are allowed-->
    <allowed_ips>
      <!--<ip>192.168.0.1</ip>-->
    </allowed_ips>
  </network>
  <content_directory>
    <!--a list of possible charsets can be found under:
      http://www.gnu.org/software/libiconv/-->
    <local_charset>UTF-8</local_charset>
    <!--libs used for metadata extraction when building the database. [true|false]-->
    <use_imagemagick>true</use_imagemagick>
    <use_taglib>true</use_taglib>
    <use_libavformat>true</use_libavformat>
  </content_directory>
  <global_settings>
    <temp_dir/>
    <!--uuid is written to and read from <config-dir>/uuid.txt if set to true-->
    <use_fixed_uuid>false</use_fixed_uuid>
  </global_settings>
  <device_settings>
    <!--"default" settings are inhertied by specific devices and can be overwritten-->
    <!--do NOT remove the "default" device settings-->
    <!--all new file types have to be added to the default settings-->
    <!--adding new file types just to a specific device will have no affect-->
    <device name="default">
      <!--specify the maximum length for file names (0 or empty = unlimited)-->
      <max_file_name_length>0</max_file_name_length>
      <!--[file|container]-->
      <playlist_style>file</playlist_style>
      <show_childcount_in_title>false</show_childcount_in_title>
      <enable_dlna>false</enable_dlna>
      <transcoding_release_delay>4</transcoding_release_delay>
      <file_settings>
        <!--audio files-->
        <file ext="mp3">
          <type>AUDIO_ITEM</type>
          <mime_type>audio/mpeg</mime_type>
          <dlna>MP3</dlna>
        </file>
        <file ext="ogg">
          <type>AUDIO_ITEM</type>
          <mime_type>application/octet-stream</mime_type>
          <transcode enabled="true">
            <ext>mp3</ext>
            <mime_type>audio/mpeg</mime_type>
            <dlna>MP3</dlna>
            <http_encoding>chunked</http_encoding>
            <decoder>vorbis</decoder>
            <encoder>lame</encoder>
            <bitrate>192</bitrate>
            <samplerate>44100</samplerate>
          </transcode>
        </file>
        <file ext="mpc">
          <type>AUDIO_ITEM</type>
          <mime_type>application/octet-stream</mime_type>
          <transcode enabled="true">
            <ext>mp3</ext>
            <mime_type>audio/mpeg</mime_type>
            <dlna>MP3</dlna>
            <http_encoding>chunked</http_encoding>
            <decoder>musepack</decoder>
            <encoder>lame</encoder>
            <bitrate>192</bitrate>
            <samplerate>44100</samplerate>
          </transcode>
        </file>
        <file ext="wav">
          <type>AUDIO_ITEM</type>
          <mime_type>audio/x-wav</mime_type>
        </file>
        <file ext="flac">
          <type>AUDIO_ITEM</type>
          <mime_type>audio/x-flac</mime_type>
          <transcode enabled="true">
            <ext>mp3</ext>
            <mime_type>audio/mpeg</mime_type>
            <dlna>MP3</dlna>
            <http_encoding>chunked</http_encoding>
            <decoder>flac</decoder>
            <encoder>lame</encoder>
            <bitrate>192</bitrate>
            <samplerate>44100</samplerate>
          </transcode>
        </file>
        <file ext="wma">
          <type>AUDIO_ITEM</type>
          <mime_type>audio/x-ms-wma</mime_type>
          <dlna>WMAFULL</dlna>
        </file>
        <!--image files-->
        <file ext="jpg">
          <ext>jpeg</ext>
          <type>IMAGE_ITEM</type>
          <mime_type>image/jpeg</mime_type>
          <convert enabled="false">
            <!--<dcraw enabled="true">-q 0</dcraw>-->
            <ext>png</ext>
            <mime_type>image/png</mime_type>
            <height>0</height>
            <width>0</width>
            <!--set "greater" to "true" if you only want to resize images greater than "height" or "width"-->
            <greater>false</greater>
            <!--set "less" to "true" if you only want to resize images less than "height" or "width"-->
            <less>false</less>
            <!--set "less" and "greater" to "false" if you always want to resize-->
          </convert>
        </file>
        <file ext="bmp">
          <type>IMAGE_ITEM</type>
          <mime_type>image/bmp</mime_type>
        </file>
        <file ext="png">
          <type>IMAGE_ITEM</type>
          <mime_type>image/png</mime_type>
        </file>
        <file ext="gif">
          <type>IMAGE_ITEM</type>
          <mime_type>image/gif</mime_type>
        </file>
        <!--video files-->
        <file ext="mpg">
          <ext>mpeg</ext>
          <type>VIDEO_ITEM</type>
          <mime_type>video/mpeg</mime_type>
        </file>
        <file ext="mp4">
          <type>VIDEO_ITEM</type>
          <mime_type>video/mp4</mime_type>
        </file>
        <file ext="avi">
          <type>VIDEO_ITEM</type>
          <mime_type>video/x-msvideo</mime_type>
        </file>
        <file ext="wmv">
          <type>VIDEO_ITEM</type>
          <mime_type>video/x-ms-wmv</mime_type>
        </file>
        <file ext="vob">
          <type>VIDEO_ITEM</type>
          <mime_type>video/x-ms-vob</mime_type>
        </file>
        <file ext="vdr">
          <type>VIDEO_ITEM</type>
          <mime_type>video/x-extension-vdr</mime_type>
          <transcode enabled="true">
            <ext>vob</ext>
            <mime_type>video/x-ms-vob</mime_type>
          </transcode>
        </file>
        <file ext="flv">
          <type>VIDEO_ITEM</type>
          <mime_type>application/x-flash-video</mime_type>
        </file>
        <file ext="asf">
          <type>VIDEO_ITEM</type>
          <mime_type>video/x-ms-asf</mime_type>
        </file>
        <!--playlists-->
        <file ext="pls">
          <type>PLAYLIST</type>
          <mime_type>audio/x-scpls</mime_type>
        </file>
        <file ext="m3u">
          <type>PLAYLIST</type>
          <mime_type>audio/x-mpegurl</mime_type>
        </file>
      </file_settings>
    </device>
    <!--For other device settings take a look at http://fuppes.ulrich-voelkel.de/wiki/index.php/Category:Device-->
    <!--If you have more than one device it is a good idea to set the ip address as some devices may have conflicting "user agents".-->
    <!--It is safe to remove unneeded devices-->
    <device name="PS3" enabled="false">
      <user_agent>UPnP/1.0 DLNADOC/1.00</user_agent>
      <user_agent>PLAYSTATION3</user_agent>
      <!--<ip></ip>-->
      <enable_dlna>true</enable_dlna>
      <transcoding_release_delay>50</transcoding_release_delay>
      <file_settings>
        <file ext="ogg">
          <type>AUDIO_ITEM_MUSIC_TRACK</type>
          <transcode enabled="true">
            <http_encoding>stream</http_encoding>
          </transcode>
        </file>
      </file_settings>
    </device>
    <device name="Xbox 360" virtual="Xbox 360" enabled="false">
      <user_agent>Xbox/2.0.\d+.\d+ UPnP/1.0 Xbox/2.0.\d+.\d+</user_agent>
      <user_agent>Xenon</user_agent>
      <xbox360>true</xbox360>
      <show_empty_resolution>true</show_empty_resolution>
      <description_values>
        <friendly_name>%s %v : 1 : Windows Media Connect</friendly_name>
        <model_name>Windows Media Connect compatible (%s)</model_name>
        <model_number>2.0</model_number>
      </description_values>
    </device>
  </device_settings>
</fuppes_config>

---

### Post by BrokenKingpin on 2008-07-26
I fixed my problem... I needed to install taglib.

---

### Post by revjtanton on 2008-08-09
So I'm getting a hodge-podge of errors and I can't seem to find the problem.  I've forwarded traffic through my router, as far as I know, correctly.  The Xbox 360 sees fuppes, and lists my movies, however everything times out.  It doesn't give me errors about cannot play the file or whatever, but it gives me errors stating the connection with the PC was lost...wtf?  Posted for your view pleasure is my fuppes.config file and vfolder.config file


fuppes.config:
```
<?xml version="1.0" encoding="UTF-8"?>
<fuppes_config version="0.7.2.3">
  <shared_objects>
    <dir>/media/White Rabbit</dir>
    <!--<dir>/mnt/music</dir>-->
    <!--<itunes>/Users/.../iTunes.xml</itunes>-->
    <dir>/home/jt</dir>
    <dir>/home/jt/Videos</dir>
    <dir>/home/jt/Temp</dir>
  </shared_objects>
  <network>
    <!--empty = automatic detection-->
    <interface>eth0</interface>
    <!--empty or 0 = random port-->
    <http_port>8080</http_port>
    <!--list of ip addresses allowed to access fuppes. if empty all ips are allowed-->
    <allowed_ips>
      <ip>192.168.1.102</ip>
    </allowed_ips>
  </network>
  <content_directory>
    <!--a list of possible charsets can be found under:
      http://www.gnu.org/software/libiconv/-->
    <local_charset>UTF-8</local_charset>
    <!--libs used for metadata extraction when building the database. [true|false]-->
    <use_imagemagick>true</use_imagemagick>
    <use_taglib>true</use_taglib>
    <use_libavformat>true</use_libavformat>
  </content_directory>
  <transcoding>
    <!--[lame|twolame]-->
    <audio_encoder>lame</audio_encoder>
    <!--[true|false]-->
    <transcode_vorbis>true</transcode_vorbis>
    <transcode_musepack>true</transcode_musepack>
    <transcode_flac>true</transcode_flac>
  </transcoding>
  <device_settings>
    <!--"default" settings are inhertied by specific devices and can be overwritten-->
    <!--do NOT remove the "default" device settings-->
    <device name="default">z
      <!--specify the maximum length for file names (0 or empty = unlimited)-->
      <max_file_name_length>0</max_file_name_length>
      <!--[file|container]-->
      <playlist_style>file</playlist_style>
      <show_childcount_in_title>false</show_childcount_in_title>
      <enable_dlna>false</enable_dlna>
      <transcoding_release_delay>4</transcoding_release_delay>
      <file_settings><!--audio files--><file ext="mp3"><type>AUDIO_ITEM</type><mime_type>audio/mpeg</mime_type><dlna>MP3</dlna></file>
	<file ext="ogg"><type>AUDIO_ITEM</type><mime_type>application/octet-stream</mime_type><transcode enabled="true"><ext>mp3</ext><mime_type>audio/mpeg</mime_type><dlna>MP3</dlna><http_encoding>chunked</http_encoding><decoder>vorbis</decoder><encoder>lame</encoder><bitrate>192</bitrate><samplerate>44100</samplerate></transcode></file>
	<file ext="mpc"><type>AUDIO_ITEM</type><mime_type>application/octet-stream</mime_type><transcode enabled="true"><ext>mp3</ext><mime_type>audio/mpeg</mime_type><dlna>MP3</dlna><http_encoding>chunked</http_encoding><decoder>musepack</decoder><encoder>lame</encoder><bitrate>192</bitrate><samplerate>44100</samplerate></transcode></file>
	<file ext="wav"><type>AUDIO_ITEM</type><mime_type>audio/x-wav</mime_type></file><file ext="flac"><type>AUDIO_ITEM</type><mime_type>audio/x-flac</mime_type><transcode enabled="true"><ext>mp3</ext><mime_type>audio/mpeg</mime_type><dlna>MP3</dlna><http_encoding>chunked</http_encoding><decoder>flac</decoder><encoder>lame</encoder><bitrate>192</bitrate><samplerate>44100</samplerate></transcode></file>
	<file ext="wma"><type>AUDIO_ITEM</type><mime_type>audio/x-ms-wma</mime_type><dlna>WMAFULL</dlna></file>

<!--image files--><file ext="jpg"><ext>jpeg</ext><type>IMAGE_ITEM</type><mime_type>image/jpeg</mime_type><convert enabled="false"><!--<dcraw enabled="true">-q 0</dcraw>--><ext>png</ext><mime_type>image/png</mime_type><height>0</height><width>0</width><!--set "greater" to "true" if you only want to resize images greater than "height" or "width"--><greater>false</greater><!--set "less" to "true" if you only want to resize images less than "height" or "width"--><less>false</less><!--set "less" and "greater" to "false" if you always want to resize--></convert></file><file ext="bmp"><type>IMAGE_ITEM</type><mime_type>image/bmp</mime_type></file>
	<file ext="png"><type>IMAGE_ITEM</type><mime_type>image/png</mime_type></file><file ext="gif"><type>IMAGE_ITEM</type><mime_type>image/gif</mime_type></file>

<!--video files--><file ext="mpg"><ext>mpeg</ext><type>VIDEO_ITEM</type><mime_type>video/mpeg</mime_type></file><file ext="mp4"><type>VIDEO_ITEM</type><mime_type>video/mp4</mime_type></file>
	<file ext="avi"><type>VIDEO_ITEM</type><mime_type>video/x-msvideo</mime_type></file>
	<file ext="wmv"><type>VIDEO_ITEM</type><mime_type>video/x-ms-wmv</mime_type></file><file ext="vob"><type>VIDEO_ITEM</type><mime_type>video/x-ms-vob</mime_type></file>
	<file ext="vdr"><type>VIDEO_ITEM</type><mime_type>video/x-extension-vdr</mime_type><transcode enabled="true"><ext>vob</ext><mime_type>video/x-ms-vob</mime_type></transcode></file>
	<file ext="flv"><type>VIDEO_ITEM</type><mime_type>application/x-flash-video</mime_type></file><file ext="asf"><type>VIDEO_ITEM</type><mime_type>video/x-ms-asf</mime_type></file>

 <!--playlists--><file ext="pls"><type>PLAYLIST</type><mime_type>audio/x-scpls</mime_type></file><file ext="m3u"><type>PLAYLIST</type><mime_type>audio/x-mpegurl</mime_type></file></file_settings>
    </device>
    <!--If you have more than one device it is a good idea to set the ip address manually as some devices may have conflicting "user agents".-->
    <!--It is safe to remove unneeded devices-->
    <device name="PS3" enabled="false">
      <user_agent>UPnP/1.0 DLNADOC/1.00</user_agent>
      <user_agent>PLAYSTATION3</user_agent>
      <!--<ip></ip>-->
      <enable_dlna>true</enable_dlna>
      <transcoding_release_delay>50</transcoding_release_delay>
      <file_settings>
        <file ext="ogg">
          <type>AUDIO_ITEM_MUSIC_TRACK</type>
          <transcode enabled="true">
            <http_encoding>stream</http_encoding>
          </transcode>
        </file>
      </file_settings>
    </device>
    <device name="Xbox 360" virtual="Xbox 360" enabled="true">
      <user_agent>Xbox/2.0.\d+.\d+ UPnP/1.0 Xbox/2.0.\d+.\d+</user_agent>
      <user_agent>Xenon</user_agent>
      <xbox360>true</xbox360>
      <file_settings>
        <file ext="mp3">
          <type>AUDIO_ITEM_MUSIC_TRACK</type>
        </file>
        <file ext="jpg">
          <type>IMAGE_ITEM_PHOTO</type>
        </file>
        <file ext="avi">
          <type>VIDEO_ITEM</type>
          <mime_type>video/x-msvideo</mime_type>
          <transcode enabled="true">
            <transcoder>ffmpeg</transcoder>
            <ext>wmv</ext>
            <mime_type>video/x-ms-wmv</mime_type>
            <video_codec>wmv2</video_codec>
            <audio_codec>wmav1</audio_codec>
            <video_bitrate>1800000</video_bitrate>
            <audio_bitrate>128000</audio_bitrate>
          </transcode>
        </file>
      </file_settings>
      <description_values>
        <friendly_name>%s %v : 1 : Windows Media Connect</friendly_name>
        <model_name>Windows Media Connect compatible (%s)</model_name>
        <model_number>2.0</model_number>
      </description_values>
    </device>
    <device name="Noxon audio" virtual="default" enabled="false">
      <!--Please enter the address of your Noxon. Automatic detection is impossible because the Noxon does not send a "user-agent" in it's requests-->
      <!--<ip></ip>-->
      <playlist_style>container</playlist_style>
      <show_childcount_in_title>true</show_childcount_in_title>
    </device>
    <device name="Telegent TG 100" virtual="default" enabled="false">
      <user_agent>dma/1.0 \(http://www.cybertan.com.tw/\)</user_agent>
      <user_agent>UPnP/1.0 DLNADOC/1.00</user_agent>
      <playlist_style>file</playlist_style>
      <max_file_name_length>101</max_file_name_length>
    </device>
  </device_settings>
</fuppes_config>
```

and vfolder.config:
```
<?xml version="1.0" encoding="UTF-8"?>
<fuppes_vfolder_config version="0.2">

 <vfolder_layout device="default" enabled="false">

    <vfolder name="Genre">
      <vfolders property="genre">
        <items type="audioItem" />
      </vfolders>
    </vfolder>

    <vfolder name="Genre/Artists">
      <vfolders property="genre">
        <vfolders property="artist">
          <items type="audioItem" />
        </vfolders>
      </vfolders>
    </vfolder>

    <vfolder name="Artists/Albums">
      <vfolders property="artist">
        <vfolders property="album">
          <items type="audioItem" />
        </vfolders>
      </vfolders>
    </vfolder> 
    
    <vfolder name="ABC/Artists/Albums">
      <vfolders split="ABC">
        <vfolders property="artist">
          <vfolders property="album">
            <items type="audioItem" />
          </vfolders>
        </vfolders>
      </vfolders>
    </vfolder>
       
    <vfolder name="Photos">
      <vfolder name="All">
        <items type="imageItem" />
      </vfolder>
      <vfolder name="Folders">
        <folders filter="contains(imageItem)" />
      </vfolder>      
    </vfolder>

    <vfolder name="Videos">
      <vfolder name="All">
        <items type="videoItem" />
      </vfolder>
      <vfolder name="Folders">
        <folders filter="contains(videoItem)" />
      </vfolder>
    </vfolder>
    
    <vfolder name="shared dirs">
      <shared_dirs full_extend="true" />
    </vfolder>
    
  </vfolder_layout>

  <vfolder_layout device="Xbox 360" enabled="true">

    <vfolder name="Music" id="1">
      <vfolder name="Album" id="7">
        <vfolders property="album" type="container.album.musicAlbum">
          <items type="audioItem" />
        </vfolders>
      </vfolder>
            
      <vfolder name="All Music" id="4">
        <items type="audioItem" />
      </vfolder>
      
      <vfolder name="Artist" id="6">
        <vfolders property="artist" type="container.person.musicArtist">
          <items type="audioItem" />
        </vfolders>
      </vfolder>
      
      <vfolder name="Folders" id="20">
        <folders filter="contains(audioItem)" />
      </vfolder>
      
      <vfolder name="Genre" id="5">
        <vfolders property="genre" type="container.genre.musicGenre">
          <items type="audioItem" />
        </vfolders>
      </vfolder>
      
      <vfolder name="Playlist" id="15" />
    </vfolder>
   
    <vfolder name="Pictures" id="3">
      <vfolder name="Album" id="13" />
      
      <vfolder name="All Pictures" id="11">
        <items type="imageItem" />
      </vfolder>
      
      <vfolder name="Date Taken" id="12" />
      
      <vfolder name="Folders" id="22">
        <folders filter="contains(imageItem)" />
      </vfolder>
    </vfolder>

    <vfolder name="Playlists" id="18">
      <vfolder name="All Playlists" id="19" />
      <vfolder name="Folders" id="23" />
    </vfolder>

    <vfolder name="Video" id="2">
      <vfolder name="Actor" id="10">
        <folders filter="contains(videoItem)" />
      </vfolder>
      <vfolder name="Album" id="14" />
      <vfolder name="All Video" id="8">
				<items type="videoItem" />
			</vfolder>
      <vfolder name="Folders" id="21">
			   <folders filter="contains(videoItem)" />
      </vfolder>
      <vfolder name="Genre" id="9" />
    </vfolder>

  </vfolder_layout>

</fuppes_vfolder_config>

```

Any help would be hot...

---

### Post by Prestwick on 2008-08-20
Hi chaps!

Probably a *really* silly question but how good is subtitles support on this when transcoding? I understand that manual configuration via XML is a must so if it does transcode stuff with subtitles, I'll be nagging everyone for help! :D

Thanks!

---

### Post by PurposeOfReason on 2008-09-24
I'm trying to get this to work with a 360. Music is good but I can't get my .mkv's.

```
<?xml version="1.0" encoding="UTF-8"?>
<fuppes_config version="0.7.2.3">
  <shared_objects>
    <dir>/storage/movies</dir>
    <dir>/storage/music</dir>
  </shared_objects>
  <network>
    <!--empty = automatic detection-->
    <interface>eth0</interface>
    <!--empty or 0 = random port-->
    <http_port/>
    <!--list of ip addresses allowed to access fuppes. if empty all ips are allowed-->
    <allowed_ips>
    </allowed_ips>
  </network>
  <content_directory>
    <!--a list of possible charsets can be found under:
      http://www.gnu.org/software/libiconv/-->
    <local_charset>UTF-8</local_charset>
    <!--libs used for metadata extraction when building the database. [true|false]-->
    <use_imagemagick>true</use_imagemagick>
    <use_taglib>true</use_taglib>
    <use_libavformat>true</use_libavformat>
  </content_directory>
  <global_settings>
    <temp_dir/>
    <!--uuid is written to and read from <config-dir>/uuid.txt if set to true-->
    <use_fixed_uuid>true</use_fixed_uuid>
  </global_settings>
  <device_settings>
    <!--"default" settings are inhertied by specific devices and can be overwritten-->
    <!--do NOT remove the "default" device settings-->
    <!--all new file types have to be added to the default settings-->
    <!--adding new file types just to a specific device will have no affect-->
    <device name="default">
      <!--specify the maximum length for file names (0 or empty = unlimited)-->
      <max_file_name_length>0</max_file_name_length>
      <!--[file|container]-->
      <playlist_style>file</playlist_style>
      <show_childcount_in_title>false</show_childcount_in_title>
      <enable_dlna>false</enable_dlna>
      <transcoding_release_delay>4</transcoding_release_delay>
      <file_settings>
        <!--audio files-->
        <file ext="mp3">
          <type>AUDIO_ITEM</type>
          <mime_type>audio/mpeg</mime_type>
          <dlna>MP3</dlna>
        </file>
        <file ext="ogg">
          <type>AUDIO_ITEM</type>
          <mime_type>application/octet-stream</mime_type>
          <transcode enabled="true">
            <ext>mp3</ext>
            <mime_type>audio/mpeg</mime_type>
            <dlna>MP3</dlna>
            <http_encoding>chunked</http_encoding>
            <decoder>vorbis</decoder>
            <encoder>lame</encoder>
            <bitrate>192</bitrate>
            <samplerate>44100</samplerate>
          </transcode>
        </file>
        <file ext="mpc">
          <type>AUDIO_ITEM</type>
          <mime_type>application/octet-stream</mime_type>
          <transcode enabled="true">
            <ext>mp3</ext>
            <mime_type>audio/mpeg</mime_type>
            <dlna>MP3</dlna>
            <http_encoding>chunked</http_encoding>
            <decoder>musepack</decoder>
            <encoder>lame</encoder>
            <bitrate>192</bitrate>
            <samplerate>44100</samplerate>
          </transcode>
        </file>
        <file ext="wav">
          <type>AUDIO_ITEM</type>
          <mime_type>audio/x-wav</mime_type>
        </file>
        <file ext="flac">
          <type>AUDIO_ITEM</type>
          <mime_type>audio/x-flac</mime_type>
          <transcode enabled="true">
            <ext>mp3</ext>
            <mime_type>audio/mpeg</mime_type>
            <dlna>MP3</dlna>
            <http_encoding>chunked</http_encoding>
            <decoder>flac</decoder>
            <encoder>lame</encoder>
            <bitrate>192</bitrate>
            <samplerate>44100</samplerate>
          </transcode>
        </file>
        <file ext="wma">
          <type>AUDIO_ITEM</type>
          <mime_type>audio/x-ms-wma</mime_type>
          <dlna>WMAFULL</dlna>
        </file>
        <!--image files-->
        <file ext="jpg">
          <ext>jpeg</ext>
          <type>IMAGE_ITEM</type>
          <mime_type>image/jpeg</mime_type>
          <convert enabled="false">
            <!--<dcraw enabled="true">-q 0</dcraw>-->
            <ext>png</ext>
            <mime_type>image/png</mime_type>
            <height>0</height>
            <width>0</width>
            <!--set "greater" to "true" if you only want to resize images greater than "height" or "width"-->
            <greater>false</greater>
            <!--set "less" to "true" if you only want to resize images less than "height" or "width"-->
            <less>false</less>
            <!--set "less" and "greater" to "false" if you always want to resize-->
          </convert>
        </file>
        <file ext="bmp">
          <type>IMAGE_ITEM</type>
          <mime_type>image/bmp</mime_type>
        </file>
        <file ext="png">
          <type>IMAGE_ITEM</type>
          <mime_type>image/png</mime_type>
        </file>
        <file ext="gif">
          <type>IMAGE_ITEM</type>
          <mime_type>image/gif</mime_type>
        </file>
        <!--video files-->
        <file ext="mpg">
          <ext>mpeg</ext>
          <type>VIDEO_ITEM</type>
          <mime_type>video/mpeg</mime_type>
        </file>
        <file ext="mp4">
          <type>VIDEO_ITEM</type>
          <mime_type>video/mp4</mime_type>
        </file>
        <file ext="avi">
          <type>VIDEO_ITEM</type>
          <mime_type>video/x-msvideo</mime_type>
        </file>
        <file ext="wmv">
          <type>VIDEO_ITEM</type>
          <mime_type>video/x-ms-wmv</mime_type>
        </file>
        <file ext="vob">
          <type>VIDEO_ITEM</type>
          <mime_type>video/x-ms-vob</mime_type>
        </file>
        <file ext="vdr">
          <type>VIDEO_ITEM</type>
          <mime_type>video/x-extension-vdr</mime_type>
          <transcode enabled="true">
            <ext>vob</ext>
            <mime_type>video/x-ms-vob</mime_type>
          </transcode>
        </file>
        <file ext="flv">
          <type>VIDEO_ITEM</type>
          <mime_type>application/x-flash-video</mime_type>
        </file>
        <file ext="asf">
          <type>VIDEO_ITEM</type>
          <mime_type>video/x-ms-asf</mime_type>
        </file>
        <!--playlists-->
        <file ext="pls">
          <type>PLAYLIST</type>
          <mime_type>audio/x-scpls</mime_type>
        </file>
        <file ext="m3u">
          <type>PLAYLIST</type>
          <mime_type>audio/x-mpegurl</mime_type>
        </file>
      </file_settings>
    </device>
    <!--For other device settings take a look at http://fuppes.ulrich-voelkel.de/wiki/index.php/Category:Device-->
    <!--If you have more than one device it is a good idea to set the ip address as some devices may have conflicting "user agents".-->
    <!--It is safe to remove unneeded devices-->
    <device name="PS3" enabled="false">
      <user_agent>UPnP/1.0 DLNADOC/1.00</user_agent>
      <user_agent>PLAYSTATION3</user_agent>
      <!--<ip></ip>-->
      <enable_dlna>true</enable_dlna>
      <transcoding_release_delay>50</transcoding_release_delay>
      <file_settings>
        <file ext="ogg">
          <type>AUDIO_ITEM_MUSIC_TRACK</type>
          <transcode enabled="true">
            <http_encoding>stream</http_encoding>
          </transcode>
        </file>
      </file_settings>
    </device>
        <device name="Xbox 360" virtual="Xbox 360" enabled="true">

<description_values> 
<friendly_name>%s %v : 1 : Windows Media Connect</friendly_name> 
<model_name>Windows Media Connect compatible (%s)</model_name> 
<model_number>2.0</model_number> 
</description_values> 

      <user_agent>Xbox/2.0.\d+.\d+ UPnP/1.0 Xbox/2.0.\d+.\d+</user_agent>
      <user_agent>Xenon</user_agent>
      <xbox360>true</xbox360>
   <file_settings>
      <file ext="mp3"><type>AUDIO_ITEM_MUSIC_TRACK</type></file>
      <file ext="jpg"><type>IMAGE_ITEM_PHOTO</type></file>
      <file ext="avi"><type>VIDEO_ITEM</type><mime_type>video/avi</mime_type></file>
<file ext="mkv">
<type>VIDEO_ITEM</type>
<mime_type>video/x-matroska</mime_type>
<transcode enabled="true">
<transcoder>ffmpeg</transcoder>
<ext>mpg</ext>
<mime_type>video/mpeg</mime_type>
<video_codec>mpeg2video</video_codec>
<audio_codec>mp2</audio_codec>
<ffmpeg_params>-ac 2</ffmpeg_params>
<audio_bitrate>128000</audio_bitrate>
</transcode>
</file> 
    </file_settings>

    </device>
  </device_settings>
</fuppes_config>
```

---

### Post by unabatedshagie on 2008-10-05
I'm having problems getting this to compile on intrepid ibex.

If I run the command: **./configure --enable-video-transcoding --enable-gnome-panel-applet --prefix=/usr** when I run make after it I get the following error ```
make[1]: *** [libmetadata_libavformat_la-metadata_libavformat.lo] Error 1
make[1]: Leaving directory `/home/alex/Source/svn/fuppes/src/plugins'
make: *** [all-recursive] Error 1

```


however if I run the command: **./configure --enable-video-transcoding --enable-gnome-panel-applet --prefix=/usr --disable-libavformat** then make runs fine and it installs but everything on my PS3 comes up as [unsupported data]

Below is the end of the output after running ./configure
```
  SUMMARY

  audio transcoding enabled
    encoder:
      lame       : yes
      twolame    : yes
      wav        : yes
      pcm        : yes
    decoder:
      vorbis     : yes (libvorbisfile)
      mpc        : yes
      flac       : yes
      faad       : yes (aac/mp4/m4a)
      mad        : yes (mpeg Layer I, II & III)

  video transcoding plugins
    ffmpeg     : enabled

  image conversion/rescaling plugins
    ImageMagick: disabled (Magick++)

  metadata extraction plugins
    taglib        : enabled  (mp3, ogg, flac & mpc metadata extraction)
    ImageMagick   : disabled (Wand)
    simage        : disabled (jpeg, png, gif, tiff, rgb, pic, tga, eps)
    libavformat   : enabled
    mpeg4ip/mp4v2 : enabled  (mp4/m4a metadata extraction)

  miscellaneous
    iconv      : enabled (charset conversion)
    uuid       : enabled

  GNOME
    panel applet : enabled
    libnotify    : enabled

Thanks for using fuppes
please report bugs
```

I followed the instructions from [here]("http://fuppes.ulrich-voelkel.de/wiki/index.php?title=Compiling_on_Linux") when compiling it.

---

### Post by Doby on 2008-10-07
I need the svn url. The one at the beginning of the thread doesn't work and the one from fuppes doesn't work on hardy.  Anyone out there know where I can find this or what it is?

---

### Post by jeanvincent21 on 2008-10-15
This is the new svn address to use:

[https://fuppes.svn.sourceforge.net/svnroot/fuppes](https://fuppes.svn.sourceforge.net/svnroot/fuppes)

---

### Post by f1nd on 2008-10-28
hi,

sorry i cant geht fuppes to work. i want use fuppes on vmware or virtualbox. on a windows host.

but i try to compile that for more than 7 days. no chance.

can please anyone upload a small image for vmware or virtualbox.

PLS

---

### Post by teethlikelions on 2008-11-18
I am having the same problem with the error 
> make[1]: *** [libmetadata_libavformat_la-metadata_libavformat.lo] Error 1
make[1]: Leaving directory `/home/matt/fuppes/src/plugins'
make: *** [install-recursive] Error 1
I have installed ALL the *-dev dependencies for the ffmpeg package, but no luck!
what is the conscequence of compiling with the --disable-libavformat for non-PS3 users? anything mentionable?

---

### Post by Mysticaly on 2008-11-18
To the OP, thanks allot, this post finally made fuppes run for me :)

I've spent hours on getting it work, glad I found your post :)

---

### Post by linuzo on 2008-12-08
> **lmellor said:**
> here is the transcript of what happens....

```
luke@UPSTAIRS:~/fuppes$ fuppes
            FUPPES - SVN-r571
    the Free UPnP Entertainment Service
      [http://fuppes.ulrich-voelkel.de](http://fuppes.ulrich-voelkel.de)

webinterface: [http://192.168.0.2:9452](http://192.168.0.2:9452)

r = rebuild database
i = print system info
h = print help

press "ctrl-c" or "q" to quit

:1: parser warning : xmlns:ms: ' urn:microsoft-com:wmc-1-0' is not a valid URI
ot xmlns="urn:schemas-upnp-org:device-1-0" xmlns:ms=" urn:microsoft-com:wmc-1-0"
                                                                               ^
== lib/Fuppes.cpp (336) :: Sun Dec  2 16:58:09 2007 ==
new device: Xbox 360 :: MediaRenderer

new UPnP device:
Xbox 360 (MediaRenderer)
```



here is my fuppes.cfg file...

```
<?xml version="1.0" encoding="UTF-8"?>
<fuppes_config version="0.7.2.3">
  <shared_objects>
    <!--<dir>/mnt/music</dir>-->
    <!--<itunes>/Users/.../iTunes.xml</itunes>-->
    <dir>/media/sda6/Music</dir>
    <dir>/media/sda6/Large Music Vids</dir>
  </shared_objects>

  <network>
    <!--empty = automatic detection-->
    <interface>eth0</interface>
    <!--empty or 0 = random port-->
    <http_port>9452</http_port>
    <!--list of ip addresses allowed to access fuppes. if empty all ips are allowed-->
    <allowed_ips>
      <!--<ip>192.168.0.1</ip>-->
      <ip>192.168.0.63</ip>
    </allowed_ips>
  </network>
  <content_directory>
    <!--a list of possible charsets can be found under:
      http://www.gnu.org/software/libiconv/-->
    <local_charset>UTF-8</local_charset>
    <!--libs used for metadata extraction when building the database. [true|false]-->
    <use_imagemagick>true</use_imagemagick>
    <use_taglib>true</use_taglib>
    <use_libavformat>true</use_libavformat>
  </content_directory>
  <transcoding>
    <!--[lame|twolame]-->
    <audio_encoder>lame</audio_encoder>
    <!--[true|false]-->
    <transcode_vorbis>true</transcode_vorbis>
    <transcode_musepack>true</transcode_musepack>
    <transcode_flac>true</transcode_flac>
  </transcoding>
  <device_settings>
    <!--"default" settings are inhertied by specific devices and can be overwritten-->
    <device name="default">
      <!--specify the maximum length for file names (0 or empty = unlimited)-->
      <max_file_name_length>0</max_file_name_length>
      <!--[file|container]-->
      <playlist_style>file</playlist_style>
      <show_childcount_in_title>false</show_childcount_in_title>
      <enable_dlna>false</enable_dlna>
      <transcoding_release_delay>4</transcoding_release_delay>
      <file_settings>
        <!--audio files-->
        <file ext="mp3">
          <type>AUDIO_ITEM</type>
          <mime_type>audio/mpeg</mime_type>
          <dlna>MP3</dlna>
        </file>
        <file ext="ogg">
          <type>AUDIO_ITEM</type>
          <mime_type>application/octet-stream</mime_type>
          <transcode enabled="true">
            <ext>mp3</ext>
            <mime_type>audio/mpeg</mime_type>
            <dlna>MP3</dlna>
            <http_encoding>chunked</http_encoding>
            <decoder>vorbis</decoder>
            <encoder>lame</encoder>
            <bitrate>192</bitrate>
            <samplerate>44100</samplerate>
          </transcode>
        </file>
        <file ext="mpc">
          <type>AUDIO_ITEM</type>
          <mime_type>application/octet-stream</mime_type>
          <transcode enabled="true">
            <ext>mp3</ext>
            <mime_type>audio/mpeg</mime_type>
            <dlna>MP3</dlna>
            <http_encoding>chunked</http_encoding>
            <decoder>musepack</decoder>
            <encoder>lame</encoder>
            <bitrate>192</bitrate>
            <samplerate>44100</samplerate>
          </transcode>
        </file>
        <file ext="wav">
          <type>AUDIO_ITEM</type>
          <mime_type>audio/x-wav</mime_type>
        </file>
        <file ext="flac">
          <type>AUDIO_ITEM</type>
          <mime_type>audio/x-flac</mime_type>
          <transcode enabled="true">
            <ext>mp3</ext>
            <mime_type>audio/mpeg</mime_type>
            <dlna>MP3</dlna>
            <http_encoding>chunked</http_encoding>
            <decoder>flac</decoder>
            <encoder>lame</encoder>
            <bitrate>192</bitrate>
            <samplerate>44100</samplerate>
          </transcode>
        </file>
        <file ext="wma">
          <type>AUDIO_ITEM</type>
          <mime_type>audio/x-ms-wma</mime_type>
          <dlna>WMAFULL</dlna>
        </file>
        <!--image files-->
        <file ext="jpg">
          <ext>jpeg</ext>
          <type>IMAGE_ITEM</type>
          <mime_type>image/jpeg</mime_type>
          <convert enabled="false">
            <!--<dcraw enabled="true">-q 0</dcraw>-->
            <ext>png</ext>
            <mime_type>image/png</mime_type>
            <height>0</height>
            <width>0</width>
            <!--set "greater" to "true" if you only want to resize images greater than "height" or "width"-->
            <greater>false</greater>
            <!--set "less" to "true" if you only want to resize images less than "height" or "width"-->
            <less>false</less>
            <!--set "less" and "greater" to "false" if you always want to resize-->
          </convert>
        </file>
        <file ext="bmp">
          <type>IMAGE_ITEM</type>
          <mime_type>image/bmp</mime_type>
        </file>
        <file ext="png">
          <type>IMAGE_ITEM</type>
          <mime_type>image/png</mime_type>
        </file>
        <file ext="gif">
          <type>IMAGE_ITEM</type>
          <mime_type>image/gif</mime_type>
        </file>
        <!--video files-->
        <file ext="mpg">
          <ext>mpeg</ext>
          <type>VIDEO_ITEM</type>
          <mime_type>video/mpeg</mime_type>
        </file>
        <file ext="mp4">
          <type>VIDEO_ITEM</type>
          <mime_type>video/mp4</mime_type>
        </file>
        <file ext="avi">
          <type>VIDEO_ITEM</type>
          <mime_type>video/x-msvideo</mime_type>
        </file>
        <file ext="wmv">
          <type>VIDEO_ITEM</type>
          <mime_type>video/x-ms-wmv</mime_type>
        </file>
        <file ext="vob">
          <type>VIDEO_ITEM</type>
          <mime_type>video/x-ms-vob</mime_type>
        </file>
        <file ext="vdr">
          <type>VIDEO_ITEM</type>
          <mime_type>video/x-extension-vdr</mime_type>
          <transcode enabled="true">
            <ext>vob</ext>
            <mime_type>video/x-ms-vob</mime_type>
          </transcode>
        </file>
        <file ext="flv">
          <type>VIDEO_ITEM</type>
          <mime_type>application/x-flash-video</mime_type>
        </file>
        <file ext="asf">
          <type>VIDEO_ITEM</type>
          <mime_type>video/x-ms-asf</mime_type>
        </file>
        <!--playlists-->
        <file ext="pls">
          <type>PLAYLIST</type>
          <mime_type>audio/x-scpls</mime_type>
        </file>
        <file ext="m3u">
          <type>PLAYLIST</type>
          <mime_type>audio/x-mpegurl</mime_type>
        </file>
      </file_settings>
    </device>
    <!--If you have more than one device it is a good idea to set the ip address manually as some devices may have conflicting "user agents".-->
    <device name="PS3" enabled="false">
      <user_agent>UPnP/1.0 DLNADOC/1.00</user_agent>
      <user_agent>PLAYSTATION3</user_agent>
      <!--<ip></ip>-->
      <enable_dlna>true</enable_dlna>
      <transcoding_release_delay>50</transcoding_release_delay>
      <file_settings>
        <file ext="ogg">
          <type>AUDIO_ITEM_MUSIC_TRACK</type>
          <transcode enabled="true">
            <http_encoding>stream</http_encoding>
          </transcode>
        </file>
      </file_settings>
    </device>
    <device name="Xbox 360" virtual="Xbox 360" enabled="true">
        <user_agent>Xbox/2.0.\d+.\d+ UPnP/1.0 Xbox/2.0.\d+.\d+</user_agent>
        <user_agent>Xenon</user_agent>
        <xbox360>true</xbox360>
        <file_settings>
            <file ext="mp3"><type>AUDIO_ITEM_MUSIC_TRACK</type></file>
            <file ext="jpg"><type>IMAGE_ITEM_PHOTO</type></file>
            <file ext="avi">
              <type>VIDEO_ITEM</type>
              <mime_type>video/x-msvideo</mime_type>
              <transcode enabled="true">         
                <transcoder>ffmpeg</transcoder>
                <ext>wmv</ext>
                <mime_type>video/x-ms-wmv</mime_type>         
                <video_codec>wmv2</video_codec>
                <audio_codec>wmav1</audio_codec>
                <video_bitrate>1800000</video_bitrate>
                <audio_bitrate>128000</audio_bitrate>
              </transcode>
            </file>
        </file_settings>
    </device>
    <device name="Telegent TG 100" virtual="default" enabled="false">
      <user_agent>dma/1.0 \(http://www.cybertan.com.tw/\)</user_agent>
      <user_agent>UPnP/1.0 DLNADOC/1.00</user_agent>
      <playlist_style>file</playlist_style>
      <max_file_name_length>101</max_file_name_length>
    </device>
  </device_settings>
</fuppes_config>
```


and here is my vfolder.cfg file...

```
<?xml version="1.0" encoding="UTF-8"?>
<fuppes_vfolder_config version="0.2">

 <vfolder_layout device="default" enabled="false">

    <vfolder name="Genre">
      <vfolders property="genre">
        <items type="audioItem" />
      </vfolders>
    </vfolder>

    <vfolder name="Genre/Artists">
      <vfolders property="genre">
        <vfolders property="artist">
          <items type="audioItem" />
        </vfolders>
      </vfolders>
    </vfolder>

    <vfolder name="Artists/Albums">
      <vfolders property="artist">
        <vfolders property="album">
          <items type="audioItem" />
        </vfolders>
      </vfolders>
    </vfolder> 
    
    <vfolder name="ABC/Artists/Albums">
      <vfolders split="ABC">
        <vfolders property="artist">
          <vfolders property="album">
            <items type="audioItem" />
          </vfolders>
        </vfolders>
      </vfolders>
    </vfolder>
       
    <vfolder name="Photos">
      <vfolder name="All">
        <items type="imageItem" />
      </vfolder>
      <vfolder name="Folders">
        <folders filter="contains(imageItem)" />
      </vfolder>      
    </vfolder>

    <vfolder name="Videos">
      <vfolder name="All">
        <items type="videoItem" />
      </vfolder>
      <vfolder name="Folders">
        <folders filter="contains(videoItem)" />
      </vfolder>
    </vfolder>
    
    <vfolder name="shared dirs">
      <shared_dirs full_extend="true" />
    </vfolder>
    
  </vfolder_layout>

  <vfolder_layout device="Xbox 360" enabled="true">

    <vfolder name="Music" id="1">
      <vfolder name="Album" id="7">
        <vfolders property="album" type="container.album.musicAlbum">
          <items type="audioItem" />
        </vfolders>
      </vfolder>
            
      <vfolder name="All Music" id="4">
        <items type="audioItem" />
      </vfolder>
      
      <vfolder name="Artist" id="6">
        <vfolders property="artist" type="container.person.musicArtist">
          <items type="audioItem" />
        </vfolders>
      </vfolder>
      
      <vfolder name="Folders" id="20">
        <folders filter="contains(audioItem)" />
      </vfolder>
      
      <vfolder name="Genre" id="5">
        <vfolders property="genre" type="container.genre.musicGenre">
          <items type="audioItem" />
        </vfolders>
      </vfolder>
      
      <vfolder name="Playlist" id="15" />
    </vfolder>
   
    <vfolder name="Pictures" id="3">
      <vfolder name="Album" id="13" />
      
      <vfolder name="All Pictures" id="11">
        <items type="imageItem" />
      </vfolder>
      
      <vfolder name="Date Taken" id="12" />
      
      <vfolder name="Folders" id="22">
        <folders filter="contains(imageItem)" />
      </vfolder>
    </vfolder>

    <vfolder name="Playlists" id="18">
      <vfolder name="All Playlists" id="19" />
      <vfolder name="Folders" id="23" />
    </vfolder>

    <vfolder name="Video" id="2">
      <vfolder name="Actor" id="10">
        <folders filter="contains(videoItem)" />
      </vfolder>
      <vfolder name="Album" id="14" />
      <vfolder name="All Video" id="8">
				<items type="videoItem" />
			</vfolder>
      <vfolder name="Folders" id="21">
			   <folders filter="contains(videoItem)" />
      </vfolder>
      <vfolder name="Genre" id="9" />
    </vfolder>

  </vfolder_layout>

</fuppes_vfolder_config>
```


I hope this helps somehow.

(I am running 64 bit gutsy btw)


I had this same issue with the problem being that it wasn't picking up the device from eth0. Problem was fixed after I entered in my machine IP in the <interface></interface> option. My PS3 was then able to detect it and able to transcode things fine. :)  Yay finally..

---

### Post by linuzo on 2008-12-08
wasutton3, 

the reason for the errors when you are trying to start fuppes is because of your config file for fuppes. the <interface/> isn't the proper for closing a section it's </interface> as you see in the rest of the config for examples. Try fixing that if you havn't figured it out already.

---

### Post by neomaximus2k on 2008-12-22
hey guys, tried getting this to work on a new ubuntu server 8.10 and failed.. i get the following error during the configure stage


```

checking for iconv declaration...
         extern size_t iconv (iconv_t cd, char * *inbuf, size_t *inbytesleft, char * *outbuf, size_t *outbytesleft);
checking for PCRE... configure: error: Package requirements (libpcre >= 5.0) were not met:

No package 'libpcre' found

Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix.

Alternatively, you may set the environment variables PCRE_CFLAGS
and PCRE_LIBS to avoid the need to call pkg-config.
See the pkg-config man page for more details.

root@XT-SERVER:~/fuppes#

```

any ideas?


I have since got this working on 8.10 Server perfectly, I have the tutorial on how to do it as well in text just need to re-write it.  My only problem now is my 360 see's the server but no files, not folders, nothing at all.  I'm at a loss at pressent as to the cause.

I have got transcoding enabled (and for those of you who say you dont need it, fall update, blah lbah blah the fall update DOES NOT COVER ALL CODECS!!!) but even with it disabled i still see nothing.

---

### Post by andre123 on 2008-12-28
hi.. i'm having some problems with fuppes..
my ps3 doesn't find any media server when i use the search...
is there any issue with router/port forwarding or something?
in that case, what port should i forward?

i think maybe there's something wrong with my devices list on fuppes... look what i get after running sudo fuppes:

```
new device: UPNP-NAT-Gateway :: unknown

new UPnP device:
UPNP-NAT-Gateway (unknown)
== lib/Fuppes.cpp (346) :: Sun Dec 28 11:40:13 2008 ==
new device: UPNP-NAT-Gateway :: unknown

new UPnP device:
UPNP-NAT-Gateway (unknown)
== lib/Fuppes.cpp (346) :: Sun Dec 28 11:40:13 2008 ==
new device: UPNP-NAT-Gateway :: unknown

new UPnP device:
UPNP-NAT-Gateway (unknown)
webinterface: http://192.168.0.103:9137

r = rebuild database
u = update database
i = print system info
h = print help

press "ctrl-c" or "q" to quit

```

here's my fuppes.conf:

```
<?xml version="1.0" encoding="UTF-8"?>
<fuppes_config version="0.7.2.3">
 <shared_objects>
   <dir>/media/Dados2</dir>
 </shared_objects>
<network>
   <!--empty = automatic detection-->
   <interface>192.168.0.103</interface>
   <!--empty or 0 = random port-->
   <http_port>9137</http_port>
   <!--list of ip addresses allowed to access fuppes. if empty all ips are allowed-->
   <allowed_ips>
     <!--<ip>192.168.0.1</ip>-->
   </allowed_ips>
 </network>


 <content_directory>
<!--a list of possible charsets can be found under:
http://www.gnu.org/software/libiconv/-->
<local_charset>UTF-8</local_charset>
<!--libs used for metadata extraction when building the database. [true|false]-->
<use_imagemagick>true</use_imagemagick>
<use_taglib>true</use_taglib>
<use_libavformat>true</use_libavformat>
</content_directory>
<transcoding>
<!--[lame|twolame]-->
<audio_encoder>lame</audio_encoder>
<!--[true|false]-->
<transcode_vorbis>true</transcode_vorbis>
<transcode_musepack>true</transcode_musepack>
<transcode_flac>true</transcode_flac>
</transcoding>
<device_settings>
<!--"default" settings are inhertied by specific devices and can be overwritten-->
<!--do NOT remove the "default" device settings-->
<device name="default">
<!--specify the maximum length for file names (0 or empty = unlimited)-->
<max_file_name_length>0</max_file_name_length>
<!--[file|container]-->
<playlist_style>file</playlist_style>
<show_childcount_in_title>false</show_childcount_in_title>
<enable_dlna>false</enable_dlna>
<transcoding_release_delay>4</transcoding_release_delay>
<file_settings>
<!--audio files-->
<file ext="mp3">
<type>AUDIO_ITEM</type>
<mime_type>audio/mpeg</mime_type>
<dlna>MP3</dlna>
</file>
<file ext="ogg">
<type>AUDIO_ITEM</type>
<mime_type>application/octet-stream</mime_type>
<transcode enabled="true">
<ext>mp3</ext>
<mime_type>audio/mpeg</mime_type>
<dlna>MP3</dlna>
<http_encoding>chunked</http_encoding>
<decoder>vorbis</decoder>
<encoder>lame</encoder>
<bitrate>192</bitrate>
<samplerate>44100</samplerate>
</transcode>
</file>
<file ext="mpc">
<type>AUDIO_ITEM</type>
<mime_type>application/octet-stream</mime_type>
<transcode enabled="true">
<ext>mp3</ext>
<mime_type>audio/mpeg</mime_type>
<dlna>MP3</dlna>
<http_encoding>chunked</http_encoding>
<decoder>musepack</decoder>
<encoder>lame</encoder>
<bitrate>192</bitrate>
<samplerate>44100</samplerate>
</transcode>
</file>
<file ext="wav">
<type>AUDIO_ITEM</type>
<mime_type>audio/x-wav</mime_type>
</file>
<file ext="flac">
<type>AUDIO_ITEM</type>
<mime_type>audio/x-flac</mime_type>
<transcode enabled="true">
<ext>mp3</ext>
<mime_type>audio/mpeg</mime_type>
<dlna>MP3</dlna>
<http_encoding>chunked</http_encoding>
<decoder>flac</decoder>
<encoder>lame</encoder>
<bitrate>192</bitrate>
<samplerate>44100</samplerate>
</transcode>
</file>
<file ext="wma">
<type>AUDIO_ITEM</type>
<mime_type>audio/x-ms-wma</mime_type>
<dlna>WMAFULL</dlna>
</file>
<!--image files-->
<file ext="jpg">
<ext>jpeg</ext>
<type>IMAGE_ITEM</type>
<mime_type>image/jpeg</mime_type>
<convert enabled="false">
<!--<dcraw enabled="true">-q 0</dcraw>-->
<ext>png</ext>
<mime_type>image/png</mime_type>
<height>0</height>
<width>0</width>
<!--set "greater" to "true" if you only want to resize images greater than "height" or "width"-->
<greater>false</greater>
<!--set "less" to "true" if you only want to resize images less than "height" or "width"-->
<less>false</less>
<!--set "less" and "greater" to "false" if you always want to resize-->
</convert>
</file>
<file ext="bmp">
<type>IMAGE_ITEM</type>
<mime_type>image/bmp</mime_type>
</file>
<file ext="png">
<type>IMAGE_ITEM</type>
<mime_type>image/png</mime_type>
</file>
<file ext="gif">
<type>IMAGE_ITEM</type>
<mime_type>image/gif</mime_type>
</file>
<!--video files-->
<file ext="mpg">
<ext>mpeg</ext>
<type>VIDEO_ITEM</type>
<mime_type>video/mpeg</mime_type>
</file>
<file ext="mp4">
<type>VIDEO_ITEM</type>
<mime_type>video/mp4</mime_type>
</file>
<file ext="avi">
<type>VIDEO_ITEM</type>
<mime_type>video/x-msvideo</mime_type>
</file>
<file ext="wmv">
<type>VIDEO_ITEM</type>
<mime_type>video/x-ms-wmv</mime_type>
</file>
<file ext="vob">
<type>VIDEO_ITEM</type>
<mime_type>video/x-ms-vob</mime_type>
</file>
<file ext="vdr">
<type>VIDEO_ITEM</type>
<mime_type>video/x-extension-vdr</mime_type>
<transcode enabled="true">
<ext>vob</ext>
<mime_type>video/x-ms-vob</mime_type>
</transcode>
</file>
<file ext="flv">
<type>VIDEO_ITEM</type>
<mime_type>application/x-flash-video</mime_type>
</file>
<file ext="asf">
<type>VIDEO_ITEM</type>
<mime_type>video/x-ms-asf</mime_type>
</file>
<!--playlists-->
<file ext="pls">
<type>PLAYLIST</type>
<mime_type>audio/x-scpls</mime_type>
</file>
<file ext="m3u">
<type>PLAYLIST</type>
<mime_type>audio/x-mpegurl</mime_type>
</file>
</file_settings>
</device>
<!--If you have more than one device it is a good idea to set the ip address manually as some devices may have conflicting "user agents".-->
<!--It is safe to remove unneeded devices-->
<device name="PS3" enabled="false">
<user_agent>UPnP/1.0 DLNADOC/1.00</user_agent>
<user_agent>PLAYSTATION3</user_agent>
<!--<ip>192.168.0.6</ip>-->
<enable_dlna>true</enable_dlna>
<transcoding_release_delay>50</transcoding_release_delay>
<file_settings>
<file ext="ogg">
<type>item.audioItem.musicTrack</type>
<transcode enabled="true">
<http_encoding>stream</http_encoding>
</transcode>
</file>
<file ext="mpg">
<type>VIDEO_ITEM</type>
<transcode enabled="true">
<transcoder>ffmpeg</transcoder>
<mime_type>video/mpeg</mime_type>
<ext>mpg</ext>
<video_codec>copy</video_codec>
<audio_codec>mp2</audio_codec>
<audio_samplerate>44100</audio_samplerate>
<audio_bitrate>192000</audio_bitrate>
</transcode>
</file>
<file ext="avi">
<type>VIDEO_ITEM</type>
<mime_type>video/x-divx</mime_type>
<transcode enabled="true">
<transcoder>ffmpeg</transcoder>
<ext>mpg</ext>
<mime_type>video/mpeg</mime_type>
<video_codec vcodec="msmpeg4">mpeg1video</video_codec>
<video_bitrate>1800000</video_bitrate>
<audio_codec acodec="wmav2">mp2</audio_codec>
<audio_samplerate>44100</audio_samplerate>
<audio_bitrate>192000</audio_bitrate>
</transcode>
</file>
<file ext="mkv">
<type>VIDEO_ITEM</type>
<mime_type>video/x-matroska</mime_type>
<transcode enabled="true">
<transcoder>ffmpeg</transcoder>
<ext>mpg</ext>
<mime_type>video/mpeg</mime_type>
<video_codec>mpeg2video</video_codec>
<video_bitrate>1800000</video_bitrate>
<audio_codec>mp2</audio_codec>
<audio_samplerate>44100</audio_samplerate>
<audio_bitrate>192000</audio_bitrate>
</transcode>
</file>
<file ext="avi">
<type>VIDEO_ITEM</type>
<mime_type>video/x-msvideo</mime_type>
<transcode enabled="true">
<transcoder>ffmpeg</transcoder>
<ext>mpg</ext>
<mime_type>video/mpeg</mime_type>
<video_codec>mpeg2video</video_codec>
<video_bitrate>1800000</video_bitrate>
<audio_codec>mp2</audio_codec>
<audio_samplerate>44100</audio_samplerate>
<audio_bitrate>192000</audio_bitrate>
</transcode>
</file>
</file_settings>
</device>
<device name="Xbox 360" virtual="Xbox 360" enabled="false">
<user_agent>Xbox/2.0.\d+.\d+ UPnP/1.0 Xbox/2.0.\d+.\d+</user_agent>
<user_agent>Xenon</user_agent>
<xbox360>true</xbox360>
</device>
<device name="Noxon audio" virtual="default" enabled="false">
<!--Please enter the address of your Noxon. Automatic detection is impossible because the Noxon does not send a "user-agent" in it's requests-->
<!--<ip></ip>-->
<playlist_style>container</playlist_style>
<show_childcount_in_title>true</show_childcount_in_title>
</device>
<device name="Telegent TG 100" virtual="default" enabled="false">
<user_agent>dma/1.0 \(http://www.cybertan.com.tw/\)</user_agent>
<user_agent>UPnP/1.0 DLNADOC/1.00</user_agent>
<playlist_style>file</playlist_style>
<max_file_name_length>101</max_file_name_length>
</device>
</device_settings>
</fuppes_config>

```

and my vfolder.cfg

```
<?xml version="1.0" encoding="UTF-8"?>
<fuppes_vfolder_config version="0.2">

 <vfolder_layout device="default" enabled="false">

    <vfolder name="Genre">
      <vfolders property="genre">
        <items type="audioItem" />
      </vfolders>
    </vfolder>

    <vfolder name="Genre/Artists">
      <vfolders property="genre">
        <vfolders property="artist">
          <items type="audioItem" />
        </vfolders>
      </vfolders>
    </vfolder>

    <vfolder name="Artists/Albums">
      <vfolders property="artist">
        <vfolders property="album">
          <items type="audioItem" />
        </vfolders>
      </vfolders>
    </vfolder> 
    
    <vfolder name="ABC/Artists/Albums">
      <vfolders split="ABC">
        <vfolders property="artist">
          <vfolders property="album">
            <items type="audioItem" />
          </vfolders>
        </vfolders>
      </vfolders>
    </vfolder>
       
    <vfolder name="Photos">
      <vfolder name="All">
        <items type="imageItem" />
      </vfolder>
      <vfolder name="Folders">
        <folders filter="contains(imageItem)" />
      </vfolder>      
    </vfolder>

    <vfolder name="Videos">
      <vfolder name="All">
        <items type="videoItem" />
      </vfolder>
      <vfolder name="Folders">
        <folders filter="contains(videoItem)" />
      </vfolder>
    </vfolder>
    
    <vfolder name="shared dirs">
      <shared_dirs full_extend="true" />
    </vfolder>
    
  </vfolder_layout>

  <vfolder_layout device="Xbox 360" enabled="true">

    <vfolder name="Music" id="1">
      <vfolder name="Album" id="7">
        <vfolders property="album" type="container.album.musicAlbum">
          <items type="audioItem" />
        </vfolders>
      </vfolder>
            
      <vfolder name="All Music" id="4">
        <items type="audioItem" />
      </vfolder>
      
      <vfolder name="Artist" id="6">
        <vfolders property="artist" type="container.person.musicArtist">
          <items type="audioItem" />
        </vfolders>
      </vfolder>
      
      <vfolder name="Folders" id="20">
        <folders filter="contains(audioItem)" />
      </vfolder>
      
      <vfolder name="Genre" id="5">
        <vfolders property="genre" type="container.genre.musicGenre">
          <items type="audioItem" />
        </vfolders>
      </vfolder>
      
      <vfolder name="Playlist" id="15" />
    </vfolder>
   
    <vfolder name="Pictures" id="3">
      <vfolder name="Album" id="13" />
      
      <vfolder name="All Pictures" id="11">
        <items type="imageItem" />
      </vfolder>
      
      <vfolder name="Date Taken" id="12" />
      
      <vfolder name="Folders" id="22">
        <folders filter="contains(imageItem)" />
      </vfolder>
    </vfolder>

    <vfolder name="Playlists" id="18">
      <vfolder name="All Playlists" id="19" />
      <vfolder name="Folders" id="23" />
    </vfolder>

    <vfolder name="Video" id="2">
      <vfolder name="Actor" id="10">
        <folders filter="contains(videoItem)" />
      </vfolder>
      <vfolder name="Album" id="14" />
      <vfolder name="All Video" id="8">
				<items type="videoItem" />
			</vfolder>
      <vfolder name="Folders" id="21">
			   <folders filter="contains(videoItem)" />
      </vfolder>
      <vfolder name="Genre" id="9" />
    </vfolder>

  </vfolder_layout>

</fuppes_vfolder_config>

```

any help would be appreciated!

edit: whoa, i managed somehow to connect my ps3 to the fuppes server. can even play .mp3 files, but now i have a nem problem: .avi files doesn't play and shows as unsupported data, and .mkv files can't be seen whyle browsing the folders on the ps3.

---

### Post by neomaximus2k on 2008-12-28
well your PS3 wasn't listed in the devices that might be why it wasn't originally working, as for your new problem try disabling transcoding, for some reason if you enable transcoding the video files disappear, no idea why

---

### Post by andre123 on 2008-12-29
> **neomaximus2k said:**
> well your PS3 wasn't listed in the devices that might be why it wasn't originally working, as for your new problem try disabling transcoding, for some reason if you enable transcoding the video files disappear, no idea why

i'll try that... thanks

edit: okey, disabling trancode did the trick to some .avi files... now i can play then but mkv files are not dettected and some avi shows as unsupported data.

how can i upscale the video to fit my tv width? the playback has very thick back borders..

---

### Post by neomaximus2k on 2008-12-29
> **andre123 said:**
> i'll try that... thanks

edit: okey, disabling trancode did the trick to some .avi files... now i can play then but mkv files are not dettected and some avi shows as unsupported data.

how can i upscale the video to fit my tv width? the playback has very thick back borders..

Sadly I haven't found the way of getting transcoding working AND show the files on the list,  I did notice the web interface stated that transcoding is off as it couldn't find the transcoder despite lame being installed so perhaps it is something to do with this.

I have the same issue with MKV Files, sadly i convert them to AVI files myself and the black borders, well on the 360 you an tell it to stretch the video to the screen i'm guessing you can do the same thing with the ps3

---

### Post by PorchSong on 2008-12-29
> **neomaximus2k said:**
> Sadly I haven't found the way of getting transcoding working AND show the files on the list,  I did notice the web interface stated that transcoding is off as it couldn't find the transcoder despite lame being installed so perhaps it is something to do with this.

I have the same issue with MKV Files, sadly i convert them to AVI files myself and the black borders, well on the 360 you an tell it to stretch the video to the screen i'm guessing you can do the same thing with the ps3

The reason some avi's won't play is that (on the Xbox360) it won't decode dvix 3.0 or earlier.  Thus, your vids must be divx 4.0 or greater--that shouldn't be too big a problem as only your older vids will be affected.  Only way around that is to transcode and you really do not want to do that as it kills your computer.  As for MKV, again you are SOL as the xbox and ps3 will not recognize nor decode the files.  So, you are back to transcoding.  These are not limitations of fuppes per se (fuppes doesn't recognize mkv, but it could be coded in), but really a limitation of your Xbox360/ps3.  Only solution is to transcode and that, again, kills your computer and makes for a crappy video streaming experience (difficult to fast forward, rewind, skip, etc.)

---

### Post by neomaximus2k on 2008-12-29
> **PorchSong said:**
> The reason some avi's won't play is that (on the Xbox360) it won't decode dvix 3.0 or earlier.  Thus, your vids must be divx 4.0 or greater--that shouldn't be too big a problem as only your older vids will be affected.  Only way around that is to transcode and you really do not want to do that as it kills your computer.  As for MKV, again you are SOL as the xbox and ps3 will not recognize nor decode the files.  So, you are back to transcoding.  These are not limitations of fuppes per se (fuppes doesn't recognize mkv, but it could be coded in), but really a limitation of your Xbox360/ps3.  Only solution is to transcode and that, again, kills your computer and makes for a crappy video streaming experience (difficult to fast forward, rewind, skip, etc.)

You are ocrrect about the DiVX versions and MKV however I disagree with the transcoding, I have transcoded video's from a windows vista based system for months now and not a proble,  I should also add that the same machine acts as a web server development platform and is in constant use and i've never had problems.  The only reason I moved to fuppes is because I hate the way TV Versity sets up the folders you have to enter like 4 folders before you get to your video folders you have setup its really anoying!

---

### Post by andre123 on 2008-12-29
> **neomaximus2k said:**
> Sadly I haven't found the way of getting transcoding working AND show the files on the list,  I did notice the web interface stated that transcoding is off as it couldn't find the transcoder despite lame being installed so perhaps it is something to do with this.

I have the same issue with MKV Files, sadly i convert them to AVI files myself and the black borders, well on the 360 you an tell it to stretch the video to the screen i'm guessing you can do the same thing with the ps3

you cant tell to stretch form within the xbox? not by inserting something in fuppes.cfg?

> **neomaximus2k said:**
> You are ocrrect about the DiVX versions and MKV however I disagree with the transcoding, I have transcoded video's from a windows vista based system for months now and not a proble,  I should also add that the same machine acts as a web server development platform and is in constant use and i've never had problems.  The only reason I moved to fuppes is because I hate the way TV Versity sets up the folders you have to enter like 4 folders before you get to your video folders you have setup its really anoying!

i also could transcode in a very good quality through tversity in a winxp environment. so for now, fuppes is limited for avi streaming only?

---

### Post by neomaximus2k on 2008-12-30
> **andre123 said:**
> you cant tell to stretch form within the xbox? not by inserting something in fuppes.cfg?



i also could transcode in a very good quality through tversity in a winxp environment. so for now, fuppes is limited for avi streaming only?

For the 360 if you have the remote click the display button, then I think its the 3rd or second from last button at the bottom just keep pressing ok on it until it comes up saying full (letterbox is normally the better one for me)

I think transcoding will work it is just something to do with fuppes not seeing the software is there

---

### Post by andre123 on 2008-12-30
> **neomaximus2k said:**
> For the 360 if you have the remote click the display button, then I think its the 3rd or second from last button at the bottom just keep pressing ok on it until it comes up saying full (letterbox is normally the better one for me)

I think transcoding will work it is just something to do with fuppes not seeing the software is there

and is the upscaled movie quality good? or it depends from the source?
i have a ps3, not a xbox and i'm not sure the ps3 has this option..
and if you find something out about transcoding, please tell us!!

have a happy new year!

---

### Post by neomaximus2k on 2008-12-30
> **andre123 said:**
> and is the upscaled movie quality good? or it depends from the source?
i have a ps3, not a xbox and i'm not sure the ps3 has this option..
and if you find something out about transcoding, please tell us!!

have a happy new year!

Quality depends on the source but I have every season of stargate sg1 and atlantis in avi format and watch those in letterbox mode and lets face it there are a lot of VFX in those and I dont loose any quality at all!

i'd be surprised if the ps3 doesn't have this option as 99% of players allow you to stretch the video to the current screen size while keeping the aspect ratio.

I have spoken to the main developer of fuppes to see if he can offer advice but it does look like its the way the fuppes is compiled, the method I followed I ended up changing as I noticed a lot of libraries missing as well hence the reason this tutorial lists more than others

---

### Post by andre123 on 2009-01-01
hey guys, i've found a very good alternative for media server. it's called ps3 media server and can be found here: [http://ps3mediaserver.blogspot.com/](http://ps3mediaserver.blogspot.com/)

even a linux noob like me could make it effortlessly.. all you need is mencoder package installed. you get it by doing the following:

```
sudo apt-get install mencoder
```

after that, download the latest version of ps3media server, unzip it anywhere and run PMS.sh by doing:

```

sudo chmod 775 /path/PMS.sh
sudo sh PMS.sh

``` 

and it's done! add some folders you want to share and go try it!

---

### Post by falken78 on 2009-01-12
Just some good news - I got fuppes to work with my Xbox 360 (work = Pictures, Music and Movies all play well now).

Short overview (sorry that I do not have all details) of what I did:

1. Install fuppes as stated here in the start of this post. (I hade to install several packages before I got 100% OK on the ./configuration steps..
2. Go to fuppes Forum and get the working 360 configuration files
Here is the link:
[http://fuppes.ulrich-voelkel.de/forum/viewtopic.php?f=7&t=37](http://fuppes.ulrich-voelkel.de/forum/viewtopic.php?f=7&t=37)
3. Adjust the settings to your needs (shares and network)
4. Rock n Roll!

I am using Ubuntu Interpid 8.10 i386
:guitar:

---

### Post by neomaximus2k on 2009-01-12
> **falken78 said:**
> Just some good news - I got fuppes to work with my Xbox 360 (work = Pictures, Music and Movies all play well now).

Short overview (sorry that I do not have all details) of what I did:

1. Install fuppes as stated here in the start of this post. (I hade to install several packages before I got 100% OK on the ./configuration steps..
2. Go to fuppes Forum and get the working 360 configuration files
Here is the link:
[http://fuppes.ulrich-voelkel.de/forum/viewtopic.php?f=7&t=37](http://fuppes.ulrich-voelkel.de/forum/viewtopic.php?f=7&t=37)
3. Adjust the settings to your needs (shares and network)
4. Rock n Roll!

I am using Ubuntu Interpid 8.10 i386
:guitar:


Did you get transcoding working as thats the thing that stops most people getting their fuppes working

---

### Post by nossifer on 2009-01-25
Hi.  grateful for any help.  running 8.10 and followed the instructions
I'm no expert, but I can copy and paste with the best of them.


sudo make install
Making install in src
make[1]: Entering directory `/home/chris/Desktop/fuppes-SVN-578/src'
if test -e "../version.sh"; then \
		../version.sh; \
	fi
make  install-am
make[2]: Entering directory `/home/chris/Desktop/fuppes-SVN-578/src'
/bin/bash ../libtool --tag=CXX   --mode=compile g++ -DHAVE_CONFIG_H -I. -D__STDC_CONSTANT_MACROS -I/usr/include/ffmpeg    -I/usr/include/libxml2       -DINOTIFY_THREAD_SAFE    -g -O2 -MT UDPSocket.lo -MD -MP -MF .deps/UDPSocket.Tpo -c -o UDPSocket.lo `test -f 'lib/SSDP/UDPSocket.cpp' || echo './'`lib/SSDP/UDPSocket.cpp
libtool: compile:  g++ -DHAVE_CONFIG_H -I. -D__STDC_CONSTANT_MACROS -I/usr/include/ffmpeg -I/usr/include/libxml2 -DINOTIFY_THREAD_SAFE -g -O2 -MT UDPSocket.lo -MD -MP -MF .deps/UDPSocket.Tpo -c lib/SSDP/UDPSocket.cpp  -fPIC -DPIC -o .libs/UDPSocket.o
lib/SSDP/UDPSocket.cpp: In member function ‘bool CUDPSocket::SetupSocket(bool, std::string)’:
lib/SSDP/UDPSocket.cpp:58: warning: deprecated conversion from string constant to ‘char*’
lib/SSDP/UDPSocket.cpp:71: warning: deprecated conversion from string constant to ‘char*’
lib/SSDP/UDPSocket.cpp:93: error: ‘memset’ was not declared in this scope
lib/SSDP/UDPSocket.cpp:98: warning: deprecated conversion from string constant to ‘char*’
lib/SSDP/UDPSocket.cpp:115: warning: deprecated conversion from string constant to ‘char*’
lib/SSDP/UDPSocket.cpp: In member function ‘void CUDPSocket::SendMulticast(std::string)’:
lib/SSDP/UDPSocket.cpp:165: error: ‘memset’ was not declared in this scope
lib/SSDP/UDPSocket.cpp:168: error: ‘strlen’ was not declared in this scope
lib/SSDP/UDPSocket.cpp: In member function ‘void CUDPSocket::SendUnicast(std::string, sockaddr_in)’:
lib/SSDP/UDPSocket.cpp:175: error: ‘strlen’ was not declared in this scope
make[2]: *** [UDPSocket.lo] Error 1
make[2]: Leaving directory `/home/chris/Desktop/fuppes-SVN-578/src'
make[1]: *** [install] Error 2
make[1]: Leaving directory `/home/chris/Desktop/fuppes-SVN-578/src'
make: *** [install-recursive] Error 1

---

### Post by mattisking on 2009-01-28
terry_gardener: I think I love you... in a totally platonic way, but still. Thanks alot. I got the latest from SVN, built using the instructions up top, used your config with only a couple minor tweaks, and it simply worked... first time. I sat myself down to prepare to duel with my machine and my PS3 for a few hours if need be to get this working and with the help here and yours it took about 5 minutes. Kudos.

---

### Post by bodark on 2009-03-11
Hey all I am having a problem getting fuppes to compile the error message I get is this when I attempt the checkinstall:

```
gcc -shared  .libs/libmetadata_libavformat_la-metadata_libavformat.o  -L/usr/local/lib -lavformat  -
Wl,-soname -Wl,libmetadata_libavformat.so.0 -o .libs/libmetadata_libavformat.so.0.0.0
/usr/bin/ld: /usr/local/lib/libavformat.a(allformats.o): relocation R_X86_64_32 against `aac_demuxer
' can not be used when making a shared object; recompile with -fPIC
/usr/local/lib/libavformat.a: could not read symbols: Bad value
collect2: ld returned 1 exit status
make[1]: *** [libmetadata_libavformat.la] Error 1
make[1]: Leaving directory `/home/smiller/fuppes/src/plugins'
make: *** [install-recursive] Error 1

****  Installation failed. Aborting package creation.

Cleaning up...OK

Bye.

```

This is revision 634 on Hardy with AMD Phenom 2 processor. I have tried recompiling and re-installing ffmpeg andall its dependancies, since I found a post on the fuppes forum suggesting that.

Also I am curious why I am missing the mysql dependancy:

```
SUMMARY

  audio transcoding enabled

    encoder:
      lame       : yes
      twolame    : yes
      wav        : yes
      pcm        : yes
    decoder:
      vorbis     : yes (libvorbisfile)
      mpc        : yes
      flac       : yes
      faad       : yes (aac/mp4/m4a)
      mad        : yes (mpeg Layer I, II & III)

  video transcoding plugins
    ffmpeg     : enabled

  image conversion/rescaling plugins
    ImageMagick: enabled  (Wand C-API)

  metadata extraction plugins
    taglib        : enabled  (mp3, ogg, flac & mpc metadata extraction)
    ImageMagick   : enabled  (Wand C-API)
    Exiv2         : enabled
    libavformat   : enabled
    mpeg4ip/mp4v2 : enabled  (mp4/m4a metadata extraction)

  miscellaneous
    iconv      : enabled (charset conversion)
    uuid       : enabled
    mysql      : disabled

Thanks for using fuppes

``` 

even though I have sqlite3 and sqlite3-dev installed.

my configure is this:

```
./configure --enable-gnome-panel-applet --prefix=/usr --enable-video-transcoding
```

and my ffmpeg configure is this:

```
./configure --enable-gpl --enable-postproc --enable-pthreads --enable-libfaac --
enable-libfaad --enable-libmp3lame --enable-libtheora --enable-libx264 --enable-
libxvid
```

If there is any other information I am missing please let me know.

Thanks in advance!

Edit: Also here is my ffmpeg --version info:

```
smiller@MilServ:~/ffmpeg$ ffmpeg --version
FFmpeg version SVN-r17933, Copyright (c) 2000-2009 Fabrice Bellard, et al.
  configuration: --enable-gpl --enable-postproc --enable-pthreads --enable-libfaac --enable-libfaad --enable-libmp3lame --enable-libtheora --enable-libx264 --enable-libxvid
  libavutil     50. 0. 0 / 50. 0. 0
  libavcodec    52.21. 0 / 52.21. 0
  libavformat   52.31. 1 / 52.31. 1
  libavdevice   52. 1. 0 / 52. 1. 0
  libswscale     0. 7. 1 /  0. 7. 1
  libpostproc   51. 2. 0 / 51. 2. 0
  built on Mar 11 2009 02:13:36, gcc: 4.2.4 (Ubuntu 4.2.4-1ubuntu3)
ffmpeg: missing argument for option '--version'

```

---

### Post by bodark on 2009-03-12
anyone have any ideas?

---

### Post by KoningKo on 2009-03-18
Ran into some problems getting it to compile on Ubuntu 8.10 x64.

Here is how I fixed them:
- **First I followed the instructions posted by the thread starter**

The first problem here is that the svn location has changed.
To get the latest version from svn use:
```
svn co https://fuppes.svn.sourceforge.net/svnroot/fuppes/trunk fuppes

```

- **Then autoreconf -vfi returned with an error**
I'm guessing this was caused by automake. The thing is, I wasn't able to install or uninstall it.
When trying to uninstall it with apt-get remove I got the message it wasn't installed, yet with apt-get install, I got the message it was already installed:confused:

I was finally able to uninstall and reinstall via the Synaptic package manager.

-**I also uninstalled and reinstalled some additional tools**
After some googeling I found out that autoconf and gettext could also be causing troubles.

```
$ sudo apt-get remove autoconf
$ sudo apt-get remove gettext
```

```
$ sudo apt-get install autoconf
$ sudo apt-get install gettext
```

-**Compiling**
```
$ svn co https://fuppes.svn.sourceforge.net/svnroot/fuppes/trunk fuppes
$ cd fuppes
$ autoreconf -vfi
$ ./configure --enable-video-transcoding
$ make
$ sudo make install
```

-**Additional troubles**
After installation, I tried running fuppes from console, this returned:
> fuppes: error while loading shared libraries: libfuppes.so.0: cannot open shared object file: No such file or directory

This can be solved by simply running
```
$ sudo ldconfig
```

After all that, fuppes ran fine :guitar:

Tip: you can find pre made config files here: [http://fuppes.ulrich-voelkel.de/forum/viewtopic.php?f=7&t=37](http://fuppes.ulrich-voelkel.de/forum/viewtopic.php?f=7&t=37)
Appear to work fine for my 360.

---

### Post by thecheeks on 2009-04-09
Anyone manage to get MKV transcoding on-the-fly to PS3 and/or Xbox 360?

Doesn't seem like anyone is having luck there.

---

### Post by Jesst3r on 2009-05-02
I'm having problems getting my 360 to see Video files.  I can get to the Videos directory, but the 360 just says that no files exist.

I got the latest version (636 I believe) from the svn repository and followed the installation procedure here: [http://fuppes.ulrich-voelkel.de/download/](http://fuppes.ulrich-voelkel.de/download/) .  I didn't enable transcoding because I only have avi files and I was under the impression that the 360 could now handle those without problems.

Should I try recompiling with transcoding on, even though I'm only trying to play avi? 

Also, could someone post working 360 fuppes.cfg and vfolder.cfg files?  The link to the fuppes site doesn't work anymore since there's a message about the forum being locked due to spam.  I've been using the ones that come with the latest version and I may be missing something important.

Thanks all.

Edit:  turns out I'm an idiot and put the FILE_TYPES section outside of the 360 DEVICE section.  Now everything works fine without having to recompile with transcoding since I'm only playing AVIs.  

Oh, and just a tip for those who may be as daft as me.  Make sure you copy the vfolder.cfg file into the same directory as fuppes.cfg.  THEN make sure you read both config files carefully because if you're like me, you'll miss the fact that the 360 sections have "enabled=false".  I r smrt!!

---

### Post by acme64 on 2009-08-22
the link [http://fuppes.ulrich-voelkel.de/forum/viewtopic.php?f=7&t=37](http://fuppes.ulrich-voelkel.de/forum/viewtopic.php?f=7&t=37) is dead anyone have a mirror?

On my config the xbox see's the fuppes server, but when i open it it fails. doesn't even load the stuff inside.

---

### Post by nhasian on 2009-08-23
I know its called PS3 Media server, but it works better on the xbox360 than anything else i've ever tried.  it plays divx/xvid natively to the 360 and transcodes mkv files as well for full 1080p videos:

grab the latest version ehre:

[http://ps3mediaserver.org/forum/viewtopic.php?f=2&t=3217](http://ps3mediaserver.org/forum/viewtopic.php?f=2&t=3217)

---

### Post by acme64 on 2009-08-28
ps3 media server desyncs mkv's over time, by the end of the movie the audio is off by 2 seconds or so

---

### Post by Chrus on 2009-08-28
> **acme64 said:**
> the link [http://fuppes.ulrich-voelkel.de/forum/viewtopic.php?f=7&t=37](http://fuppes.ulrich-voelkel.de/forum/viewtopic.php?f=7&t=37) is dead anyone have a mirror?

On my config the xbox see's the fuppes server, but when i open it it fails. doesn't even load the stuff inside.


Can you get to the web interface? If you can, try rebuilding your database and virtual container. If not, theres something else wrong.

---

### Post by nhasian on 2009-08-30
are you sure its not your video file?  I know sometimes they audio can be off by a second or two from the source.  you can fix it manually by using avidemux.  

anyway i've never had any problems using PS3 Media server.  I'm using version 1.11.350 on 64bit Ubuntu Karmic Alpha 4.

> **acme64 said:**
> ps3 media server desyncs mkv's over time, by the end of the movie the audio is off by 2 seconds or so

---

### Post by burntresistor on 2009-09-06
THe link to the  >  Download my vfolder.cfg and put it in the same directory as fuppes.cfg:
[http://canutes.net/fuppes/2/vfolder.cfg](http://canutes.net/fuppes/2/vfolder.cfg)   is no longer active. Any where else I can get this file

---

### Post by dn* on 2009-09-07
> **nhasian said:**
> I know its called PS3 Media server, but it works better on the xbox360 than anything else i've ever tried.  it plays divx/xvid natively to the 360 and transcodes mkv files as well for full 1080p videos:

grab the latest version ehre:

[http://ps3mediaserver.org/forum/viewtopic.php?f=2&t=3217](http://ps3mediaserver.org/forum/viewtopic.php?f=2&t=3217)

Thanks!

---

### Post by burntresistor on 2009-09-07
I've been working on this on and off the last few days. fuppes didn't create a vfolder.cfg when I installed it what could be causing this? I didn't receive any errors in the make install. I have all the dependencies.

 ```
          FUPPES - 0.640
    the Free UPnP Entertainment Service
      http://fuppes.ulrich-voelkel.de

== lib/ContentDirectory/VirtualContainerMgr.cpp (56) :: Mon Sep  7 16:50:50 2009 ==
no vfolder.cfg file available

webinterface: http://192.168.1.101:8080

r = rebuild database
u = update database
i = print system info
h = print help

press "ctrl-c" or "q" to quit


```

---

### Post by burntresistor on 2009-09-08
Bump  somewhere along the lines of following the guide I went wrong i dunno where

```

[FFmpeg version 0.5-svn17737+3:0.svn20090303-1ubuntu6, Copyright (c) 2000-2009 Fabrice Bellard, et al.
  configuration: --enable-gpl --enable-postproc --enable-swscale --enable-x11grab --extra-version=svn17737+3:0.svn20090303-1ubuntu6 --prefix=/usr --enable-avfilter --enable-avfilter-lavf --enable-libgsm --enable-libschroedinger --enable-libspeex --enable-libtheora --enable-libvorbis --enable-pthreads --disable-stripping --disable-vhook --enable-libdc1394 --enable-shared --disable-static
  libavutil     49.15. 0 / 49.15. 0
  libavcodec    52.20. 0 / 52.20. 0
  libavformat   52.31. 0 / 52.31. 0
  libavdevice   52. 1. 0 / 52. 1. 0
  libavfilter    0. 4. 0 /  0. 4. 0
  libswscale     0. 7. 1 /  0. 7. 1
  libpostproc   51. 2. 0 / 51. 2. 0
  built on Apr 10 2009 23:20:33, gcc: 4.3.3

```

my configure

```

autoreconf: Entering directory `.'
autoreconf: configure.ac: not using Gettext
autoreconf: running: aclocal --force -I m4
autoreconf: configure.ac: tracing
autoreconf: running: libtoolize --install --copy --force
libtoolize: putting auxiliary files in `.'.
libtoolize: copying file `./config.guess'
libtoolize: copying file `./config.sub'
libtoolize: copying file `./install-sh'
libtoolize: copying file `./ltmain.sh'
libtoolize: putting macros in AC_CONFIG_MACRO_DIR, `m4'.
libtoolize: copying file `m4/libtool.m4'
libtoolize: copying file `m4/ltoptions.m4'
libtoolize: copying file `m4/ltsugar.m4'
libtoolize: copying file `m4/ltversion.m4'
libtoolize: copying file `m4/lt~obsolete.m4'
autoreconf: running: /usr/bin/autoconf --force
autoreconf: running: /usr/bin/autoheader --force
autoreconf: running: automake --add-missing --copy --force-missing
Makefile.am:35: whitespace following trailing backslash
autoreconf: Leaving directory `.'

configure: WARNING: unrecognized options: --enable-video-transcoding
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for a thread-safe mkdir -p... /bin/mkdir -p
checking for gawk... gawk
checking whether make sets $(MAKE)... yes
checking for gcc... gcc
checking for C compiler default output file name... a.out
checking whether the C compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables... 
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ISO C89... none needed
checking for style of include used by make... GNU
checking dependency style of gcc... gcc3
checking for g++... g++
checking whether we are using the GNU C++ compiler... yes
checking whether g++ accepts -g... yes
checking dependency style of g++... gcc3
checking build system type... x86_64-unknown-linux-gnu
checking host system type... x86_64-unknown-linux-gnu
checking for a sed that does not truncate output... /bin/sed
checking for grep that handles long lines and -e... /bin/grep
checking for egrep... /bin/grep -E
checking for fgrep... /bin/grep -F
checking for ld used by gcc... /usr/bin/ld
checking if the linker (/usr/bin/ld) is GNU ld... yes
checking for BSD- or MS-compatible name lister (nm)... /usr/bin/nm -B
checking the name lister (/usr/bin/nm -B) interface... BSD nm
checking whether ln -s works... yes
checking the maximum length of command line arguments... 1572864
checking whether the shell understands some XSI constructs... yes
checking whether the shell understands "+="... yes
checking for /usr/bin/ld option to reload object files... -r
checking for objdump... objdump
checking how to recognize dependent libraries... pass_all
checking for ar... ar
checking for strip... strip
checking for ranlib... ranlib
checking command to parse /usr/bin/nm -B output from gcc object... ok
checking how to run the C preprocessor... gcc -E
checking for ANSI C header files... yes
checking for sys/types.h... yes
checking for sys/stat.h... yes
checking for stdlib.h... yes
checking for string.h... yes
checking for memory.h... yes
checking for strings.h... yes
checking for inttypes.h... yes
checking for stdint.h... yes
checking for unistd.h... yes
checking for dlfcn.h... yes
checking whether we are using the GNU C++ compiler... (cached) yes
checking whether g++ accepts -g... (cached) yes
checking dependency style of g++... (cached) gcc3
checking how to run the C++ preprocessor... g++ -E
checking for objdir... .libs
checking if gcc supports -fno-rtti -fno-exceptions... no
checking for gcc option to produce PIC... -fPIC -DPIC
checking if gcc PIC flag -fPIC -DPIC works... yes
checking if gcc static flag -static works... yes
checking if gcc supports -c -o file.o... yes
checking if gcc supports -c -o file.o... (cached) yes
checking whether the gcc linker (/usr/bin/ld -m elf_x86_64) supports shared libraries... yes
checking whether -lc should be explicitly linked in... no
checking dynamic linker characteristics... GNU/Linux ld.so
checking how to hardcode library paths into programs... immediate
checking whether stripping libraries is possible... yes
checking if libtool supports shared libraries... yes
checking whether to build shared libraries... yes
checking whether to build static libraries... no
checking for ld used by g++... /usr/bin/ld -m elf_x86_64
checking if the linker (/usr/bin/ld -m elf_x86_64) is GNU ld... yes
checking whether the g++ linker (/usr/bin/ld -m elf_x86_64) supports shared libraries... yes
checking for g++ option to produce PIC... -fPIC -DPIC
checking if g++ PIC flag -fPIC -DPIC works... yes
checking if g++ static flag -static works... yes
checking if g++ supports -c -o file.o... yes
checking if g++ supports -c -o file.o... (cached) yes
checking whether the g++ linker (/usr/bin/ld -m elf_x86_64) supports shared libraries... yes
checking dynamic linker characteristics... GNU/Linux ld.so
checking how to hardcode library paths into programs... immediate
checking for a BSD-compatible install... /usr/bin/install -c
checking for _LARGEFILE_SOURCE value needed for large files... no
checking for off_t... yes
checking for special C compiler options needed for large files... no
checking for _FILE_OFFSET_BITS value needed for large files... no
checking whether byte ordering is bigendian... no
checking for pkg-config... /usr/bin/pkg-config
checking pkg-config is at least version 0.9.0... yes
checking whether we are building with mingw... no
checking for dirent.h that defines DIR... yes
checking for library containing opendir... none required
checking for ANSI C header files... (cached) yes
checking arpa/inet.h usability... yes
checking arpa/inet.h presence... yes
checking for arpa/inet.h... yes
checking fcntl.h usability... yes
checking fcntl.h presence... yes
checking for fcntl.h... yes
checking netdb.h usability... yes
checking netdb.h presence... yes
checking for netdb.h... yes
checking netinet/in.h usability... yes
checking netinet/in.h presence... yes
checking for netinet/in.h... yes
checking for string.h... (cached) yes
checking sys/ioctl.h usability... yes
checking sys/ioctl.h presence... yes
checking for sys/ioctl.h... yes
checking sys/param.h usability... yes
checking sys/param.h presence... yes
checking for sys/param.h... yes
checking sys/socket.h usability... yes
checking sys/socket.h presence... yes
checking for sys/socket.h... yes
checking for unistd.h... (cached) yes
checking sys/utsname.h usability... yes
checking sys/utsname.h presence... yes
checking for sys/utsname.h... yes
checking syslog.h usability... yes
checking syslog.h presence... yes
checking for syslog.h... yes
checking for select... yes
checking size of off_t... 8
checking size of long long int... 8
checking size of unsigned long long int... 8
checking size of long int... 8
checking size of unsigned long int... 8
checking size of int... 4
checking size of unsigned int... 4
checking size of short... 2
checking size of unsigned short... 2

check minimum dependencies

checking for PCRE... yes
checking for LIBXML... yes
checking for SQLITE3... yes
checking for pthread_create in -lpthread... yes

check recommended dependencies

checking for UUID... no
checking for ld used by GCC... /usr/bin/ld -m elf_x86_64
checking if the linker (/usr/bin/ld -m elf_x86_64) is GNU ld... yes
checking for shared library run path origin... done
checking for iconv... yes
checking for working iconv... yes
checking for iconv declaration... 
         extern size_t iconv (iconv_t cd, char * *inbuf, size_t *inbytesleft, char * *outbuf, size_t *outbytesleft);

check optional stuff

checking for taglib-config... no
checking for IMAGEMAGICK_WAND... no
checking for EXIV2... no
checking for LIBAVFORMAT... yes
checking libavformat/avformat.h usability... yes
checking libavformat/avformat.h presence... yes
checking for libavformat/avformat.h... yes
checking for LIBSWSCALE... no
checking libavutil/avstring.h usability... yes
checking libavutil/avstring.h presence... yes
checking for libavutil/avstring.h... yes
checking for LIBAVCODEC... yes
checking for LIBAVUTIL... yes
checking for mpeg4ip-config... no
configure: *** mpeg4ip/libmp4v2 support disabled ***
checking for VORBISFILE... yes
checking mpcdec/config_types.h usability... no
checking mpcdec/config_types.h presence... no
checking for mpcdec/config_types.h... no
checking FLAC/file_decoder.h usability... no
checking FLAC/file_decoder.h presence... no
checking for FLAC/file_decoder.h... no
checking FLAC/stream_decoder.h usability... no
checking FLAC/stream_decoder.h presence... no
checking for FLAC/stream_decoder.h... no
checking for simage-config... no
checking for mysql_config... no
checking sys/inotify.h usability... yes
checking sys/inotify.h presence... yes
checking for sys/inotify.h... yes
configure: creating ./config.status
config.status: creating Makefile
config.status: creating m4/Makefile
config.status: creating src/Makefile
config.status: creating src/plugins/Makefile
config.status: creating src/windows/Makefile
config.status: creating src/config.h
config.status: src/config.h is unchanged
config.status: executing depfiles commands
config.status: executing libtool commands
configure: WARNING: unrecognized options: --enable-video-transcoding

  SUMMARY

  audio transcoding plugins
    encoder:
      lame       : no
      twolame    : no
      pcm/wav    : yes
    decoder:
      vorbis     : yes (libvorbisfile)
      mpc        : no
      flac       : no
      faad       : no (aac/mp4/m4a)
      mad        : no (mpeg Layer I, II & III)

  video transcoding plugins
    ffmpeg     : enabled

  image conversion/rescaling plugins
    ImageMagick: disabled (Wand C-API)

  audio metadata extraction plugins
    taglib        : disabled (mp3, ogg, flac & mpc)
    mpeg4ip/mp4v2 : disabled (mp4/m4a)

  image metadata extraction plugins
    Exiv2         : disabled
    ImageMagick   : disabled (Wand C-API)
    simage        : disabled (jpeg, png, gif, tiff, rgb, pic, tga, eps)

  video metadata extraction plugins
    libavformat   : enabled

  miscellaneous
    iconv      : enabled (charset conversion)
    uuid       : disabled
    inotify    : enabled

Thanks for using fuppes
please report bugs

```

I have most those codecs mentioned as disabled or no installed ](*,)  I assume its that went wrong cause xbox will not see it 

config.cfg
```


<?xml version="1.0" encoding="UTF-8"?>
<fuppes_config version="0.7.2.3">
  <shared_objects>
    <!--<dir>/mnt/music</dir>-->
   
<!--<itunes>/Users/.../iTunes.xml</itunes>-->
  <dir>/media/My Book/mkv and psp</dir> 
 </shared_objects>
  <network>
      
    <interface>eth1</interface>
    <http_port>0</http_port>
  <allowed_ips>
      <!--<ip></ip>-->
      <ip></ip>
    </allowed_ips>

  </network>
  <content_directory>
    <!--a list of possible charsets can be found under:
      http://www.gnu.org/software/libiconv/-->
    <local_charset>UTF-8</local_charset>
    <!--libs used for metadata extraction when building the database. [true|false]-->
    <use_imagemagick>true</use_imagemagick>
    <use_taglib>true</use_taglib>
    <use_libavformat>true</use_libavformat>
  </content_directory>
  <global_settings>
    <temp_dir/>
    <!--uuid is written to and read from <config-dir>/uuid.txt if set to true-->
    <use_fixed_uuid>false</use_fixed_uuid>
  </global_settings>
  <device_settings>
    <!--"default" settings are inhertied by specific devices and can be overwritten-->
    <!--do NOT remove the "default" device settings-->
    <!--all new file types have to be added to the default settings-->
    <!--adding new file types just to a specific device will have no affect-->
    <device name="default">
      <!--specify the maximum length for file names (0 or empty = unlimited)-->
      <max_file_name_length>0</max_file_name_length>
      <!--[file|container]-->
      <playlist_style>file</playlist_style>
      <show_childcount_in_title>false</show_childcount_in_title>
      <enable_dlna>false</enable_dlna>
      <transcoding_release_delay>4</transcoding_release_delay>
      <file_settings>
        <!--audio files-->
        <file ext="mp3">
          <type>AUDIO_ITEM</type>
          <mime_type>audio/mpeg</mime_type>
          <dlna>MP3</dlna>
        </file>
        <file ext="ogg">
          <type>AUDIO_ITEM</type>
          <mime_type>application/octet-stream</mime_type>
          <transcode enabled="true">
            <ext>mp3</ext>
            <mime_type>audio/mpeg</mime_type>
            <dlna>MP3</dlna>
            <http_encoding>chunked</http_encoding>
            <decoder>vorbis</decoder>
            <encoder>lame</encoder>
            <bitrate>192</bitrate>
            <samplerate>44100</samplerate>
          </transcode>
        </file>
        <file ext="mpc">
          <type>AUDIO_ITEM</type>
          <mime_type>application/octet-stream</mime_type>
          <transcode enabled="true">
            <ext>mp3</ext>
            <mime_type>audio/mpeg</mime_type>
            <dlna>MP3</dlna>
            <http_encoding>chunked</http_encoding>
            <decoder>musepack</decoder>
            <encoder>lame</encoder>
            <bitrate>192</bitrate>
            <samplerate>44100</samplerate>
          </transcode>
        </file>
        <file ext="wav">
          <type>AUDIO_ITEM</type>
          <mime_type>audio/x-wav</mime_type>
        </file>
        <file ext="flac">
          <type>AUDIO_ITEM</type>
          <mime_type>audio/x-flac</mime_type>
          <transcode enabled="true">
            <ext>mp3</ext>
            <mime_type>audio/mpeg</mime_type>
            <dlna>MP3</dlna>
            <http_encoding>chunked</http_encoding>
            <decoder>flac</decoder>
            <encoder>lame</encoder>
            <bitrate>192</bitrate>
            <samplerate>44100</samplerate>
          </transcode>
        </file>
        <file ext="wma">
          <type>AUDIO_ITEM</type>
          <mime_type>audio/x-ms-wma</mime_type>
          <dlna>WMAFULL</dlna>
        </file>
        <!--image files-->
        <file ext="jpg">
          <ext>jpeg</ext>
          <type>IMAGE_ITEM</type>
          <mime_type>image/jpeg</mime_type>
          <convert enabled="false">
            <!--<dcraw enabled="true">-q 0</dcraw>-->
            <ext>png</ext>
            <mime_type>image/png</mime_type>
            <height>0</height>
            <width>0</width>
            <!--set "greater" to "true" if you only want to resize images greater than "height" or "width"-->
            <greater>false</greater>
            <!--set "less" to "true" if you only want to resize images less than "height" or "width"-->
            <less>false</less>
            <!--set "less" and "greater" to "false" if you always want to resize-->
          </convert>
        </file>
        <file ext="bmp">
          <type>IMAGE_ITEM</type>
          <mime_type>image/bmp</mime_type>
        </file>
        <file ext="png">
          <type>IMAGE_ITEM</type>
          <mime_type>image/png</mime_type>
        </file>
        <file ext="gif">
          <type>IMAGE_ITEM</type>
          <mime_type>image/gif</mime_type>
        </file>
        <!--video files-->
        <file ext="mpg">
          <ext>mpeg</ext>
          <type>VIDEO_ITEM</type>
          <mime_type>video/mpeg</mime_type>
        </file>
        <file ext="mp4">
          <type>VIDEO_ITEM</type>
          <mime_type>video/mp4</mime_type>
        </file>
        <file ext="avi">
          <type>VIDEO_ITEM</type>
          <mime_type>video/x-msvideo</mime_type>
        </file>
        <file ext="wmv">
          <type>VIDEO_ITEM</type>
          <mime_type>video/x-ms-wmv</mime_type>
        </file>
        <file ext="vob">
          <type>VIDEO_ITEM</type>
          <mime_type>video/x-ms-vob</mime_type>
        </file>
        <file ext="vdr">
          <type>VIDEO_ITEM</type>
          <mime_type>video/x-extension-vdr</mime_type>
          <transcode enabled="true">
            <ext>vob</ext>
            <mime_type>video/x-ms-vob</mime_type>
          </transcode>
        </file>
        <file ext="flv">
          <type>VIDEO_ITEM</type>
          <mime_type>application/x-flash-video</mime_type>
        </file>
        <file ext="asf">
          <type>VIDEO_ITEM</type>
          <mime_type>video/x-ms-asf</mime_type>
        </file>
        <!--playlists-->
        <file ext="pls">
          <type>PLAYLIST</type>
          <mime_type>audio/x-scpls</mime_type>
        </file>
        <file ext="m3u">
          <type>PLAYLIST</type>
          <mime_type>audio/x-mpegurl</mime_type>
        </file>
      </file_settings>
    </device>
    <!--For other device settings take a look at http://fuppes.ulrich-voelkel.de/wiki/index.php/Category:Device-->
    <!--If you have more than one device it is a good idea to set the ip address as some devices may have conflicting "user agents".-->
    <!--It is safe to remove unneeded devices-->
    <device name="PS3" enabled="false">
      <user_agent>UPnP/1.0 DLNADOC/1.00</user_agent>
      <user_agent>PLAYSTATION3</user_agent>
      <!--<ip></ip>-->
      <enable_dlna>true</enable_dlna>
      <transcoding_release_delay>50</transcoding_release_delay>
      <file_settings>
        <file ext="ogg">
          <type>AUDIO_ITEM_MUSIC_TRACK</type>
          <transcode enabled="true">
            <http_encoding>stream</http_encoding>
          </transcode>
        </file>
      </file_settings>
    </device>
     <device name="Xbox 360" virtual="Xbox 360" enabled="true">
        <user_agent>Xbox/2.0.\d+.\d+ UPnP/1.0 Xbox/2.0.\d+.\d+</user_agent>
        <user_agent>Xenon</user_agent>
        <xbox360>true</xbox360>
        <file_settings>
            <file ext="mp3"><type>AUDIO_ITEM_MUSIC_TRACK</type></file>
            <file ext="jpg"><type>IMAGE_ITEM_PHOTO</type></file>
            <file ext="avi">
              <type>VIDEO_ITEM</type>
              <mime_type>video/x-msvideo</mime_type>
              <transcode enabled="true">         
                <transcoder>ffmpeg</transcoder>
                <ext>wmv</ext>
                <mime_type>video/x-ms-wmv</mime_type>         
                <video_codec>wmv2</video_codec>
                <audio_codec>wmav1</audio_codec>
                <video_bitrate>1800000</video_bitrate>
                <audio_bitrate>128000</audio_bitrate>
              </transcode>
            </file>
        </file_settings>
    </device>
  </device_settings>
</fuppes_config>

```
vfolder

```
<?xml version="1.0" encoding="UTF-8"?>
<fuppes_vfolder_config version="0.2">

<vfolder_layout device="Xbox 360" enabled="true" create_references="true">

<vfolder name="Genre">
<vfolders property="genre">
<items type="audioItem" />
</vfolders>
</vfolder>

<vfolder name="Genre/Artists">
<vfolders property="genre">
<vfolders property="artist">
<items type="audioItem" />
</vfolders>
</vfolders>
</vfolder>

<vfolder name="Artists/Albums">
<vfolders property="artist">
<vfolders property="album">
<items type="audioItem" />
</vfolders>
</vfolders>
</vfolder>

<vfolder name="ABC/Artists/Albums">
<vfolders split="ABC">
<vfolders property="artist">
<vfolders property="album">
<items type="audioItem" />
</vfolders>
</vfolders>
</vfolders>
</vfolder>

<vfolder name="Photos">
<vfolder name="All">
<items type="imageItem" />
</vfolder>
<vfolder name="Folders">
<folders filter="contains(imageItem)" />
</vfolder>
</vfolder>

<vfolder name="Videos">
<vfolder name="All">
<items type="videoItem" />
</vfolder>
<vfolder name="Folders">
<folders filter="contains(videoItem)" />
</vfolder>
</vfolder>

<vfolder name="shared dirs">
<shared_dirs full_extend="true" />
</vfolder>

</vfolder_layout>

<vfolder_layout device="Xbox 360" enabled="true">

<vfolder name="Music" id="1">
<vfolder name="Album" id="7">
<vfolders property="album" type="container.album.musicAlbum">
<items type="audioItem" />
</vfolders>
</vfolder>

<vfolder name="All Music" id="4">
<items type="audioItem" />
</vfolder>

<vfolder name="Artist" id="6">
<vfolders property="artist" type="container.person.musicArtist">
<items type="audioItem" />
</vfolders>
</vfolder>

<vfolder name="Folders" id="20">
<folders filter="contains(audioItem)" />
</vfolder>

<vfolder name="Genre" id="5">
<vfolders property="genre" type="container.genre.musicGenre">
<items type="audioItem" />
</vfolders>
</vfolder>

<vfolder name="Playlist" id="15" />
</vfolder>

<vfolder name="Pictures" id="3">
<vfolder name="Album" id="13" />

<vfolder name="All Pictures" id="11">
<items type="imageItem" />
</vfolder>

<vfolder name="Date Taken" id="12" />

<vfolder name="Folders" id="22">
<folders filter="contains(imageItem)" />
</vfolder>
</vfolder>

<vfolder name="Playlists" id="18">
<vfolder name="All Playlists" id="19" />
<vfolder name="Folders" id="23" />
</vfolder>

<vfolder name="Video" id="2">
<vfolder name="Actor" id="10">
<folders filter="contains(videoItem)" />
</vfolder>
<vfolder name="Album" id="14" />
<vfolder name="All Video" id="8">
<items type="videoItem" />
</vfolder>
<vfolder name="Folders" id="21">
<folders filter="contains(videoItem)" />
</vfolder>
<vfolder name="Genre" id="9" />
</vfolder>

</vfolder_layout>

</fuppes_vfolder_config>

```

```

[ContentDatabase] create database at Tue Sep  8 19:42:27 2009
read shared directories
[NULL @ 0x17ac240]Invalid and inefficient vfw-avi packed B frames detected
[mpeg4 @ 0x17ac240]frame skip 8
v
== lib/ContentDirectory/VirtualContainerMgr.cpp (170) :: Tue Sep  8 19:42:34 2009 ==
database rebuild in progress

    Last message repeated 1 times
[wmv3 @ 0x1772d90]Extra data: 8 bits left, value: 0
[NULL @ 0x17704b0]Invalid and inefficient vfw-avi packed B frames detected
    Last message repeated 24 times
[mpeg @ 0x17b0fd0]pes_ext 5A is invalid
[mpeg @ 0x17b0fd0]Could not find codec parameters (Audio: mp3, 0 channels, s16)
    Last message repeated 1 times
[mpeg @ 0x17b0fd0]Could not find codec parameters (Video: 0x0000)
[mpeg @ 0x17b0fd0]Could not find codec parameters (Audio: mp2, 0 channels, s16)
[mpeg @ 0x17b0fd0]Could not find codec parameters (Video: h264)
[mpeg @ 0x17b0fd0]Could not find codec parameters (Audio: mp2, 0 channels, s16)
[mpeg @ 0x17b0fd0]pes_ext 5A is invalid
[DONE] read shared directories
parse playlists
[DONE] parse playlists
parse iTunes databases
[DONE] parse iTunes databases
[ContentDatabase] database created at Tue Sep  8 19:42:48 2009


```

---

### Post by burntresistor on 2009-09-08
Bump i would be grateful if I got helped on this

---

### Post by kadrim on 2009-09-16
> **burntresistor said:**
> Bump i would be grateful if I got helped on this
 
 
you not only need to rebuild your database at the first start, but also rebuild the virtual folders.
 
this is done by using the fuppes-console and typing
 
**v**
 
rebuilding virtual folders may take some time, so be patient.

---

### Post by calcio1 on 2009-11-22
How can I view streaming p2p tv such as sopcast through fuppes on my television?

I know this is possible with TVersity

---

### Post by Vagabond97 on 2009-12-27
Hello,

I'm struggeling with streaming mpg from my Ubuntu Server 9.1 towards my XBOX 360. I installed fuppes and ffmpeg. Up to now I can watch movies and pictures as well as listen to mp3 that do not need to be transcoded.
Now I tried to stream mpg files towards the XBOX and see the following output from fuppes on the console:

```

WARNING: Do not run fuppes as the root user.
future versions of fuppes will not allow this
            FUPPES - 0.657
    the Free UPnP Entertainment Service
      http://fuppes.ulrich-voelkel.de

webinterface: http://192.168.178.21:9137

r = rebuild database
u = update database
i = print system info
h = print help

press "ctrl-c" or "q" to quit

[mpeg @ 0x88f1400]max_analyze_duration reached

Seems stream 0 codec frame rate differs from container frame rate: 50.00 (50/1) -> 25.00 (25/1)
Input #0, mpeg, from '/mnt/raidarr/media/video/xyz.mpg':
  Duration: 00:21:22.01, start: 0.186278, bitrate: 4106 kb/s
    Stream #0.0[0x1e0]: Video: mpeg2video, yuv420p, 720x576 [PAR 16:15 DAR 4:3], 3359 kb/s, 25 fps, 25 tbr, 90k tbn, 50 tbc
    Stream #0.1[0x1c0]: Audio: mp2, 48000 Hz, 2 channels, s16, 192 kb/s
    Stream #0.2[0x81]: Audio: ac3, 48000 Hz, stereo, s16, 384 kb/s

```whilst I get the following error message from the XBOX (translated from german):

```

This content can not be shown due to using a non supported codec. For futher information look at: www.xbox.com/support.

Statuscode: 69-80072746

```My config is the following:

```
<?xml version="1.0" encoding="UTF-8"?>
<fuppes_config version="0.7.2.3">
  <shared_objects>
    <dir>/mnt/raidarr/media/video/</dir>
  </shared_objects>

<network>
    <!--empty = automatic detection-->
    <interface>eth0</interface>
    <!--empty or 0 = random port-->
    <http_port>9137</http_port>
    <!--list of ip addresses allowed to access fuppes. if empty all ips are allowed-->
    <allowed_ips>
      <!--<ip>192.168.178.1</ip>-->
      <ip>192.168.178.21</ip>
      <ip>192.168.178.23</ip>
      <ip>192.168.178.26</ip>
    </allowed_ips>
  </network>
  <content_directory>
    <!--a list of possible charsets can be found under:
      http://www.gnu.org/software/libiconv/-->
    <local_charset>UTF-8</local_charset>
    <!--libs used for metadata extraction when building the database. [true|false]-->
    <use_imagemagick>true</use_imagemagick>
    <use_taglib>true</use_taglib>
    <use_libavformat>true</use_libavformat>
  </content_directory>
  <transcoding>
    <!--[lame|twolame]-->
    <audio_encoder>lame</audio_encoder>
    <!--[true|false]-->
    <transcode_vorbis>true</transcode_vorbis>
    <transcode_musepack>true</transcode_musepack>
    <transcode_flac>true</transcode_flac>
  </transcoding>
  <device_settings>
    <!--"default" settings are inhertied by specific devices and can be overwritten-->
    <device name="default">
      <!--specify the maximum length for file names (0 or empty = unlimited)-->
      <max_file_name_length>0</max_file_name_length>
      <!--[file|container]-->
      <playlist_style>file</playlist_style>
      <show_childcount_in_title>false</show_childcount_in_title>
      <enable_dlna>false</enable_dlna>
      <transcoding_release_delay>4</transcoding_release_delay>
      <file_settings>
        <!--audio files-->
        <file ext="mp3">
          <type>AUDIO_ITEM</type>
          <mime_type>audio/mpeg</mime_type>
          <dlna>MP3</dlna>
        </file>
        <file ext="ogg">
          <type>AUDIO_ITEM</type>
          <mime_type>application/octet-stream</mime_type>
          <transcode enabled="true">
            <ext>mp3</ext>
            <mime_type>audio/mpeg</mime_type>
            <dlna>MP3</dlna>
            <http_encoding>chunked</http_encoding>
            <decoder>vorbis</decoder>
            <encoder>lame</encoder>
            <bitrate>192</bitrate>
            <samplerate>44100</samplerate>
          </transcode>
        </file>
        <file ext="mpc">
          <type>AUDIO_ITEM</type>
          <mime_type>application/octet-stream</mime_type>
          <transcode enabled="true">
            <ext>mp3</ext>
            <mime_type>audio/mpeg</mime_type>
            <dlna>MP3</dlna>
            <http_encoding>chunked</http_encoding>
            <decoder>musepack</decoder>
            <encoder>lame</encoder>
            <bitrate>192</bitrate>
            <samplerate>44100</samplerate>
          </transcode>
        </file>
        <file ext="wav">
          <type>AUDIO_ITEM</type>
          <mime_type>audio/x-wav</mime_type>
        </file>
        <file ext="flac">
          <type>AUDIO_ITEM</type>
          <mime_type>audio/x-flac</mime_type>
          <transcode enabled="true">
            <ext>mp3</ext>
            <mime_type>audio/mpeg</mime_type>
            <dlna>MP3</dlna>
            <http_encoding>chunked</http_encoding>
            <decoder>flac</decoder>
            <encoder>lame</encoder>
            <bitrate>192</bitrate>
            <samplerate>44100</samplerate>
          </transcode>
        </file>
        <file ext="wma">
          <type>AUDIO_ITEM</type>
          <mime_type>audio/x-ms-wma</mime_type>
          <dlna>WMAFULL</dlna>
        </file>
        <!--image files-->
        <file ext="jpg">
          <ext>jpeg</ext>
          <type>IMAGE_ITEM</type>
          <mime_type>image/jpeg</mime_type>
          <convert enabled="false">
            <!--<dcraw enabled="true">-q 0</dcraw>-->
            <ext>png</ext>
            <mime_type>image/png</mime_type>
            <height>0</height>
            <width>0</width>
            <!--set "greater" to "true" if you only want to resize images greater than "height" or "width"-->
            <greater>false</greater>
            <!--set "less" to "true" if you only want to resize images less than "height" or "width"-->
            <less>false</less>
            <!--set "less" and "greater" to "false" if you always want to resize-->
          </convert>
        </file>
        <file ext="bmp">
          <type>IMAGE_ITEM</type>
          <mime_type>image/bmp</mime_type>
        </file>
        <file ext="png">
          <type>IMAGE_ITEM</type>
          <mime_type>image/png</mime_type>
        </file>
        <file ext="gif">
          <type>IMAGE_ITEM</type>
          <mime_type>image/gif</mime_type>
        </file>
        <!--video files-->
        <file ext="mpg">
          <ext>mpeg</ext>
          <type>VIDEO_ITEM</type>
          <mime_type>video/mpeg</mime_type>
        </file>
        <file ext="mp4">
          <type>VIDEO_ITEM</type>
          <mime_type>video/mp4</mime_type>
        </file>
        <file ext="avi">
          <type>VIDEO_ITEM</type>
          <mime_type>video/avi</mime_type>
        </file>
        <file ext="wmv">
          <type>VIDEO_ITEM</type>
          <mime_type>video/x-ms-wmv</mime_type>
        </file>
        <file ext="vob">
          <type>VIDEO_ITEM</type>
          <mime_type>video/x-ms-vob</mime_type>
        </file>
        <file ext="vdr">
          <type>VIDEO_ITEM</type>
          <mime_type>video/x-extension-vdr</mime_type>
          <transcode enabled="true">
            <ext>vob</ext>
            <mime_type>video/x-ms-vob</mime_type>
          </transcode>
        </file>
        <file ext="flv">
          <type>VIDEO_ITEM</type>
          <mime_type>application/x-flash-video</mime_type>
        </file>
        <file ext="asf">
          <type>VIDEO_ITEM</type>
          <mime_type>video/x-ms-asf</mime_type>
        </file>
        <!--playlists-->
        <file ext="pls">
          <type>PLAYLIST</type>
          <mime_type>audio/x-scpls</mime_type>
        </file>
        <file ext="m3u">
          <type>PLAYLIST</type>
          <mime_type>audio/x-mpegurl</mime_type>
        </file>
      </file_settings>
    </device>
    <!--If you have more than one device it is a good idea to set the ip address manually as some devices may have conflicting "user agents".-->
    <device name="PS3" enabled="false">
      <user_agent>UPnP/1.0 DLNADOC/1.00</user_agent>
      <user_agent>PLAYSTATION3</user_agent>
      <!--<ip></ip>-->
      <enable_dlna>true</enable_dlna>
      <transcoding_release_delay>50</transcoding_release_delay>
      <file_settings>
        <file ext="ogg">
          <type>AUDIO_ITEM_MUSIC_TRACK</type>
          <transcode enabled="true">
            <http_encoding>stream</http_encoding>
          </transcode>
        </file>
      </file_settings>
    </device>
    <device name="Xbox 360" virtual="Xbox 360" enabled="true">
        <user_agent>Xbox/2.0.\d+.\d+ UPnP/1.0 Xbox/2.0.\d+.\d+</user_agent>
        <user_agent>Xenon</user_agent>
        <xbox360>true</xbox360>
        <file_settings>
            <file ext="mp3">
        <type>AUDIO_ITEM_MUSIC_TRACK</type>
         </file>
            <file ext="jpg">
        <type>IMAGE_ITEM_PHOTO</type>
         </file>
            <file ext="avi">
        <type>VIDEO_ITEM</type>
        <mime_type>video/avi</mime_type>
         </file>
         <file ext="mpg">
              <type>VIDEO_ITEM</type>
              <mime_type>video/mpeg</mime_type>
        <transcode enabled="true">
              <transcoder>ffmpeg</transcoder>
          <ext>wmv</ext>
              <mime_type>video/x-ms-wmv</mime_type>
          <video_codec>wmv2</video_codec>
              <audio_codec>wmav1</audio_codec>           
              <video_bitrate>1800000</video_bitrate>
          <audio_bitrate>128000</audio_bitrate>
          </transcode>
           </file>
        </file_settings>
    <description_values>
    <friendly_name>%s %v : 1 : Windows Media Connect</friendly_name>
    <model_name>Windows Media Connect compatible (%s)</model_name>
    <model_number>2.0</model_number>
    </description_values> 
    </device>
    <device name="Telegent TG 100" virtual="default" enabled="false">
      <user_agent>dma/1.0 \(http://www.cybertan.com.tw/\)</user_agent>
      <user_agent>UPnP/1.0 DLNADOC/1.00</user_agent>
      <playlist_style>file</playlist_style>
      <max_file_name_length>101</max_file_name_length>
    </device>
  </device_settings>
</fuppes_config>

```ffmpeg has the following versions:

```

FFmpeg version SVN-r20939, Copyright (c) 2000-2009 Fabrice Bellard, et al.
  built on Dec 27 2009 18:40:09 with gcc 4.4.1
  configuration: --enable-gpl --enable-version3 --enable-nonfree --enable-pthreads --enable-libfaac --enable-libfaad --enable-libmp3lame --enable-libopencore-amrnb --enable-libopencore-amrwb --enable-libtheora --enable-libx264 --enable-libxvid --enable-x11grab
  libavutil     50. 7. 0 / 50. 7. 0
  libavcodec    52.45. 0 / 52.45. 0
  libavformat   52.44. 0 / 52.44. 0
  libavdevice   52. 2. 0 / 52. 2. 0
  libswscale     0. 7. 2 /  0. 7. 2

```Anybody that can help me on that problem?

---

### Post by Smokabowl on 2010-06-10
Never mind me, I'm an idiot. I solved my problem. THANK YOU!

---

### Post by X_Splinter on 2010-08-30
and how to stream with subtitles?

---

### Post by X_Splinter on 2010-09-05
I got this

User@PC:/etc/fuppes$ fuppes
            FUPPES - 0.675
    the Free UPnP Entertainment Service
      [http://fuppes.ulrich-voelkel.de](http://fuppes.ulrich-voelkel.de)

Shared (Base) Config File:/etc/fuppes/fuppes.cfg
[config] ERROR: The config file is deprecated.
[config] The config file failed to load properly.

Any idea?

---

### Post by tomvanbraeckel on 2010-12-26
How did you solve this ?

I'm getting the same behavior: "Seems stream 0 codec frame rate differs from container frame rate: 47.95 (48000/1001) -> 23.98 (24000/1001)"

---

### Post by abiheiri on 2011-09-22
For those trying to install it on ubuntu 10.04, I wrote notes so maybe it will help someone....

[http://forgottheaddress.blogspot.com/2011/09/building-fuppes-660-on-ubuntu-1004.html](http://forgottheaddress.blogspot.com/2011/09/building-fuppes-660-on-ubuntu-1004.html)

---

### Post by josephmc on 2011-10-03
I didn't have any luck with fuppes or mediatomb after hours of trying. I finally found Serviio. It transcoded on the fly with no problems! It's java based so cross platform was no problem.

[http://www.serviio.org](http://www.serviio.org)

There is a webui here for headless clients: [http://forum.serviio.org/viewtopic.php?f=17&t=1310](http://forum.serviio.org/viewtopic.php?f=17&t=1310)

NOTE: for the webui to work you have to change config.php to read $version_req = "0.6.0.1";

Hope that helps!

---

