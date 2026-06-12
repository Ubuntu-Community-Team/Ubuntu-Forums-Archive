---
title: "Compiling mcamip-0.7.8 on Karmic"
date: 2010-03-02
forum: Ubuntu Studio
---

### Post by afrodeity on 2010-03-02
Been following this thread [http://ubuntuforums.org/showthread.php?t=901612](http://ubuntuforums.org/showthread.php?t=901612)

Need to compile mcamip

[http://panteltje.com/panteltje/mcamip/](http://panteltje.com/panteltje/mcamip/)

```
mcamip-0.7.8$ make
if gcc -DPACKAGE_NAME=\"mcamip\" -DPACKAGE_TARNAME=\"mcamip\" -DPACKAGE_VERSION=\"0.7.8\" -DPACKAGE_STRING=\"mcamip\ 0.7.8\" -DPACKAGE_BUGREPORT=\"\" -DPACKAGE=\"mcamip\" -DVERSION=\"0.7.8\"  -I. -I.  -O2 -Wall -D_LARGEFILE_SOURCE -D_FILE_OFFSET_BITS=64   -g -O2 -MT mcamip.o -MD -MP -MF ".deps/mcamip.Tpo" -c -o mcamip.o mcamip.c; \
	then mv -f ".deps/mcamip.Tpo" ".deps/mcamip.Po"; else rm -f ".deps/mcamip.Tpo"; exit 1; fi
mcamip.c: In function &#8216;main&#8217;:
mcamip.c:569: warning: the address of &#8216;window_border_info&#8217; will always evaluate as &#8216;true&#8217;
mcamip.c:602: warning: ignoring return value of &#8216;fscanf&#8217;, declared with attribute warn_unused_result
if gcc -DPACKAGE_NAME=\"mcamip\" -DPACKAGE_TARNAME=\"mcamip\" -DPACKAGE_VERSION=\"0.7.8\" -DPACKAGE_STRING=\"mcamip\ 0.7.8\" -DPACKAGE_BUGREPORT=\"\" -DPACKAGE=\"mcamip\" -DVERSION=\"0.7.8\"  -I. -I.  -O2 -Wall -D_LARGEFILE_SOURCE -D_FILE_OFFSET_BITS=64   -g -O2 -MT x11.o -MD -MP -MF ".deps/x11.Tpo" -c -o x11.o x11.c; \
	then mv -f ".deps/x11.Tpo" ".deps/x11.Po"; else rm -f ".deps/x11.Tpo"; exit 1; fi
if gcc -DPACKAGE_NAME=\"mcamip\" -DPACKAGE_TARNAME=\"mcamip\" -DPACKAGE_VERSION=\"0.7.8\" -DPACKAGE_STRING=\"mcamip\ 0.7.8\" -DPACKAGE_BUGREPORT=\"\" -DPACKAGE=\"mcamip\" -DVERSION=\"0.7.8\"  -I. -I.  -O2 -Wall -D_LARGEFILE_SOURCE -D_FILE_OFFSET_BITS=64   -g -O2 -MT video.o -MD -MP -MF ".deps/video.Tpo" -c -o video.o video.c; \
	then mv -f ".deps/video.Tpo" ".deps/video.Po"; else rm -f ".deps/video.Tpo"; exit 1; fi
video.c: In function &#8216;process_jpeg_buffer&#8217;:
video.c:750: error: &#8216;INT_MAX&#8217; undeclared (first use in this function)
video.c:750: error: (Each undeclared identifier is reported only once
video.c:750: error: for each function it appears in.)
make: *** [video.o] Error 1

```

Anybody able to make head or tail of the Readme?

```

 mcamip-0.7.8



Please try
mcamip -h
for a list of all options and defaults.

All defaults are set as #defines in mcamip.h, you can change these if you like.

Motion detection threshold will be higher for 640x480, setting the correct level
for your situation needs some experimenting.
In motion detection only frames with sufficient change are output on the stdout (-y).
You can see if something is encoded by looking at fps displayed by mencoder.
The X windows display will always display normally.
The main purpose of the motion detection is to save big time on used disk space in encoding.
Only those frames that have sufficient change are encoded, and recorded with a time stamp.
If you use motion detection and specify the -i flag with some filename, then a semaphore file
will be created that other programs can check and take action upon.
These programs should erase the semaphore file after testing for it, and then test for
it again in a loop.

Example of using the semaphore file in bash, when using mcamip -y -c -s 5000 -i semaphore_file:

while true
do   
    { 
    if test -f semaphore_file 
        then
        echo "motion detected, do something here."

		rm semaphore_file
        fi

#   sleep 1
    }
done

       Examples for camera on IP address 10.0.0.151 port 81, and camera4 added in /etc/hosts:

The frame speed you get is what you specify with -f, default is 20 fps.
 *Please set the camera to 'automatic' in the video setup menu.*

Visual output via mplayer:
mcamip -a 10.0.0.151 -p 81 -y | mplayer -fs -

Show just a picture in X windows:
mcamip -a 10.0.0.151 -p 81 -x

Encode to mpeg4 AVI:
mcamip -a camera4 -p 81 -y -u USERNAME -w PASSWORD | mencoder -  -o title2.avi -oac copy -ovc lavc

Encode to mpeg4 AVI with on screen clock bottom middle in UTC (Greenwich time),
and set playback speed to 25 fps:
mcamip -t -f 25 -a camera4 -p 81 -x -y -g -u USERNAME -w PASSWORD | mencoder -  -o title2.avi -oac copy -ovc lavc

Encode with motion detection to an AVI file:
mcamip -e 1000 -c -u USERNAME -w PASSWORD -f 16 -t -a camera4 -p 80 -x -y |\
mencoder -  -o /huge/recording.avi -oac copy -ovc lavc


Write single frames if motion detected to ~/framedir/ , no X display:
mcamip -c -e 1000 -t -a IPADDRESS -p PORT -j -u USERNAME -w PASSWORD

You can list these in sequence with:
ls -rtl ~/frames/

And you can see the exact date to the second of a picture with for example:
ls -l --full-time mcamip.197.jpg

When storing as single frame .jpg files, a counter file 'jpeg_sequence_number' is written
to the directory where you stored the frames (~/frames or as in -d directory).
The jpg files will be numbered starting at this number, a check is always made for existing
numbers, and these are skipped.
You can set the start number by editing the file jpeg_sequence_number, or delete that file,
then the numbering will start at zero or the first free number.

The same, using a different directory for the jpg images:
mcamip -d /huge -c -e 1000 -t -a IPADDRESS -p PORT -j -u USERNAME -w PASSWORD

Display all .jpg images in sequence:
xv -wait 1 mcamip.*.jpg

Just watch the (any) camera:
mcamip -a IPADDRESS -p PORT -u USERNAME -w PASSWORD -x


Encode with ffmpeg version 0.4.8 (from 2004 02 22, some other versions seem to differ):
mcamip -x -u USERNAME -w PASSWORD -f 2 -t -a 10.0.0.151 -p 80 -y | \
ffmpeg -f yuv4mpegpipe -i - -f avi -vcodec mpeg4 -b 800 -g 300 -bf 2 -y camera4.avi

Encode with transcode (v0.6.11, later version may have different options) to DivX4,
in transcode you must specify the size, and the -z flag reverses the upside down picture: 
It uses the old DivX 4 codec, you can find it here:
ftp://panteltje.com/pub/divx_codecs/divx4linux-20011010_4.02.tgz
and the old transcode:
ftp://panteltje.com/pub/transcode/transcode-0.6.11.tar.gz
mcamip -x -u USERNAME -w PASSWORD -f 2 -t -a 10.0.0.151 -p 80 -y | \
transcode -f 2 -i /dev/fd/0 -g 320x240 -x yuv4mpeg,null -y divx4 -z -o camera4.avi


Encode with latest ffmpeg version to H264, in the background (I use this one),
if you re-start a new filename will be created.
mkdir /video
serial_number=`/bin/cat /video/mcamip_serial.txt`
/bin/echo "serial_number=$serial_number"

nice -n 19 mcamip -x -f 2 -t -a 10.0.0.151 -p 80 -u panteltje -w r2 -y 2>>~/mcamip-log | \
nice -n 19 ffmpeg -f yuv4mpegpipe -i - -f avi -vcodec h264 -b 80 -g 300 -bf 2 -y /video/camera4-$serial_number.avi \
1>/dev/zero 2>/dev/zero &

/bin/echo "updating serial number"
let serial_number=serial_number+1 
/bin/echo $serial_number > /video/mcamip_serial.txt




Send a low bandwidth AVI stream to a remote client in a one to one session using netcat:
 First have the receiver side started (this example uses port 1234, use whatever gets you past firewalls etc.).
 netcat -l -p 1234 | /usr/local/bin/mplayer -cache 80 -aspect 4:3  - 

 Then start the server side (where the camera is, with the IP address of the receiver).
 mcamip -x -u USER -w PASSWORD -f 2 -t -a CAMERA_IP_ADDRESS -p CAMERA_PORT -y | \
 ffmpeg -f yuv4mpegpipe -i - -f avi -vcodec mpeg4 -b 800 -g 300 -bf 2 -y /dev/fd/1 | \
 netcat -w 100 REMOTE_IP_ADDRESS 1234 


On screen user defined text:
As of version 0.75 (yes this one has it), mcamip support user defined on screen messages.
These will also appear in a recording when using '-y' flag.
This is the way it works:
When you specify the '-o' flag on the command line, then mcamip will check every second for a file
~/mcamip_os.txt.
If this file is found, its text will be added to the display.
The format of mcamip_os.txt is:
hpos vpos fg_red fg_green fg_blue bg_red bg_green bg_blue :Any text you like
100  100  200    100      50      50     100      200     :Hello there how are you today?

hpos and vpos are integers that refer to the horizontal and vertical position in pixels, top-left = 0,0.
If your text passes a window border (is to big to fit), then it is cut.

fg_red stands for fore-ground-red and is an unsigned integer range 0-255, same for the other colours.

Please note that when encoding tho the MJPEG tools YUV format, data is lost:
0 0
0 x
When the component signals 'u' and 'v' are calculated the average colour over 4 pixels is used.
When playback occurs (ffplay, mplayer, etc, saturated colours may 'overflow' visually.
This is not an error, but the way the bandwidth limiting system works.
(Human eye can resolve less detail for colour then for BW, as there are less receptors for colour in the eye).
But if you are close you will clearly see the text colour blur in the YUV....
Also blue is only 11 % brightness in this standard, red 30% and green 59%.
Best results you get with maximum contrast, for example yellow against black background would be
30 + 59 = 89 versus 0 (black), you can calculate yourself.
Or blue on a white background (11 against 100%).
It it possible to have multiple lines.
Lines starting with '#' are free format considered comments and will not be displayed.
If you want continuous background color, then the next line should be one character height 9 pixels lower.
The LF at the end of a line is surpressed.

Here is an example script for a scrolling text with dynamic content:

hpos=352
vpos=100
hflip=0
vflip=0

while [ 1 ]
do
	echo -n "$hpos $vpos  255 255 0  128 128 128 :" > /root/mcamip_os.txt
#	date >> /root/mcamip_os.txt
	echo -n mcamip by Jan Panteltje. >> /root/mcamip_os.txt

	if [ $hflip -eq 0 ]
	then
		let hpos=hpos-10
	else
		let hpos=hpos+10
	fi

	if [ $hpos -le -200 ]
	then
		hflip=1
	fi	
	
	if [ $hpos -ge 352 ]
	then
		hflip=0
	fi 


	if [ $vflip -eq 0 ]
	then
		let vpos=vpos-10
	else
		let vpos=vpos+10
	fi

	if [ $vpos -le 0 ]
	then
		vflip=1
	fi	
	
	if [ $vpos -ge 288 ]
	then
		vflip=0
	fi 


 sleep 1
done

The system can be used to record messages from a security system
('back door open', 'car in driveway', 'wrong access code', etc.) along with the date and time in
the video recording.
Or you could add fixed of changing (alert) text for objects in the picure.

You are 100% free how to implement this, only need to create the file ~/mcamip_os.txt for
1 second or longer.
You can remove any text by deleting ~/mcamip_os.txt.


Notes:
It seems in this version of the firmware that uses server push with video.cgi,
you need to set only ONE port open in the router to allow external access.
So in the router network translation table, if camera is at 10.0.0.151 port 80,
and you also run a web server on port 80, translate external port 81 to 10.0.0.151:80.
(You can define an other port then 81 for access of course).


Bugs:
If you get lines in the X windows picture, or multiple folded pictures on screen,
look in x11.c around line 61, and try uncommenting an other value for
display_bits, perhaps 24, then do a
make;make install



Apart from the java applet as indicated by D-Link, you can also make the camera available
(with password) on your web page like this:

<A href="http://IP_ADDRESS:PORT/video.cgi">click here for the direct cgi version, press reload if no motion</a>

Of course IP_ADDRESS and PORT must be set, and for external (non LAN) use a proper NATP translation
must be specified in the router.

```

---

