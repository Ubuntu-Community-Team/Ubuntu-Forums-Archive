---
title: "Can someone please make a deb package for SongBird 1.4.1?"
date: 2009-12-21
forum: The Cafe
---

### Post by legolas_w on 2009-12-21
Hi
Can someone with packaging knowledge make a debian package for songbird 1.4.1?
The download link for the tar.gz file is available at: [http://getsongbird.com/system-requirements.php](http://getsongbird.com/system-requirements.php)

Thanks

---

### Post by NoaHall on 2009-12-21
Why?
There's a daily repo, if you want a easy way.

---

### Post by legolas_w on 2009-12-21
The daily repo  ([https://launchpad.net/~songbird-daily/+archive/ppa](https://launchpad.net/~songbird-daily/+archive/ppa)) contains old builds and as stated is maintained by a BOT

---

### Post by Islington on 2009-12-21
build it yourself, stop trusting random debs. :)

---

### Post by cariboo on 2009-12-21
Download the source and use checkinstall to build a .deb for you. Checkinstall is in the repositories.

---

### Post by NoaHall on 2009-12-21
> **legolas_w said:**
> The daily repo  ([https://launchpad.net/~songbird-daily/+archive/ppa](https://launchpad.net/~songbird-daily/+archive/ppa)) contains old builds and as stated is maintained by a BOT

New builds.
1.6 is higher than 1.4.1
However, 1.6 is a alpha.

---

### Post by deancasino on 2009-12-21
I've spent the last hour trying to compile the darn thing to no avail. This is exactly the reason I moved to Banshee; the poor support of linux by the songbird team.

(Getdeb will have a .deb made shortly no doubt)

---

### Post by NoaHall on 2009-12-21
> **deancasino said:**
> I've spent the last hour trying to compile the darn thing to no avail. This is exactly the reason I moved to Banshee; the poor support of linux by the songbird team.

(Getdeb will have a .deb made shortly no doubt)

I did it.

---

### Post by deancasino on 2009-12-21
> **NoaHall said:**
> I did it.


oh? :) could you possibly upload it somewhere? Thank you.

---

### Post by legolas_w on 2009-12-21
> **NoaHall said:**
> I did it.

Can you please share it with us?

Thanks

---

### Post by NoaHall on 2009-12-21
No, I mean I've done it. Not made a deb. All you have to do is extract it.

---

### Post by Erich K on 2009-12-21
I made one, you can get it here: [http://skyzim.com/](http://skyzim.com/)

---

### Post by Xbehave on 2009-12-21
While it would be nice if somebody made a .deb for you, the easiest way to install mozilla software is to ~

1) download the binary version
2) unpack the tar to ~
3) make a launcher that points to the executable
4) check options so the program updates itself

a better alternative is to install it to /opt

1) download the binary version
2) sudo unpack the tar to /opt
3a) sudo ln -sv /opt/songbird/songbird /usr/local/bin (or something like that) [gets the cli working
3b) make a launcher that points to the executable
4) whenever there is a new version run as root (gksudo) and update

Note: These may run into problems when ubuntu's xulrunner is updated, before you update songbird, but
1) that will rarely happen, the mozilla builds get updates first
2) if it does just remove the folder and start redo streps 1&2

---

### Post by legolas_w on 2009-12-21
> **Erich K said:**
> I made one, you can get it here: [http://skyzim.com/](http://skyzim.com/)

Thank you very much.
I installed your version and I am getting the following error when I execute the songbird in a terminal window:

```
(songbird-bin:2743): GLib-WARNING **: g_set_prgname() called multiple times

(songbird-bin:2747): GStreamer-WARNING **: Failed to load plugin '/usr/lib/gstreamer-0.10/libresindvd.so': /usr/lib/gstreamer-0.10/libresindvd.so: undefined symbol: gst_navigation_event_parse_command

(songbird-bin:2747): GStreamer-WARNING **: Failed to load plugin '/usr/lib/gstreamer-0.10/libgsthdvparse.so': /usr/lib/gstreamer-0.10/libgsthdvparse.so: undefined symbol: _gst_debug_dump_mem

(songbird-bin:2747): GStreamer-WARNING **: Failed to load plugin '/usr/lib/gstreamer-0.10/libgstmatroska.so': /usr/lib/gstreamer-0.10/libgstmatroska.so: undefined symbol: gst_util_array_binary_search

(songbird-bin:2747): GStreamer-WARNING **: Failed to load plugin '/usr/lib/gstreamer-0.10/libgstdeinterlace.so': /usr/lib/gstreamer-0.10/libgstdeinterlace.so: undefined symbol: gst_video_format_parse_caps_interlaced

(songbird-bin:2747): GStreamer-WARNING **: Failed to load plugin '/usr/lib/gstreamer-0.10/libgstschro.so': /usr/lib/gstreamer-0.10/libgstschro.so: undefined symbol: gst_adapter_masked_scan_uint32

(songbird-bin:2747): GStreamer-WARNING **: Failed to load plugin '/usr/lib/gstreamer-0.10/libgstdv.so': /usr/lib/gstreamer-0.10/libgstdv.so: undefined symbol: gst_tag_list_new_full

(songbird-bin:2747): GStreamer-WARNING **: Failed to load plugin '/usr/lib/gstreamer-0.10/libgstmpegdemux.so': /usr/lib/gstreamer-0.10/libgstmpegdemux.so: undefined symbol: _gst_debug_dump_mem
././songbird-bin: symbol lookup error: /usr/lib/python2.6/dist-packages/gst-0.10/gst/_gst.so: undefined symbol: gst_task_pool_get_type
Could not initialize GStreamer: Error re-scanning registry , child terminated by signal

```

Do you have any solution for this?

---

### Post by pt123 on 2009-12-21
Does songbird have a feature to upload your data (esp. the Ratings) from Rhythmbox?

---

### Post by speedwell68 on 2009-12-22
> **legolas_w said:**
> The daily repo  ([https://launchpad.net/~songbird-daily/+archive/ppa](https://launchpad.net/~songbird-daily/+archive/ppa)) contains old builds and as stated is maintained by a BOT

> **NoaHall said:**
> New builds.
1.6 is higher than 1.4.1
However, 1.6 is a alpha.

Don't do this if you use the iPod support addon.  I have tried 1.4 but not all of my addons are compatible so I'll wait a while until they are updated.

---

### Post by monikgtr on 2010-01-25
> **legolas_w said:**
> 

Do you have any solution for this?



You can try this:

```
sudo rm -rf ~/.gconf/system/gstreamer
sudo rm -rf ~/.gstreamer-0.10
```

And then reboot. It fixed my rhythmbox and songbird issues... I was getting an error message about missing autoaudiosink.

---

### Post by user1397 on 2010-01-25
Like someone else said in this thread, making a quick and dirty deb is quite easy if you don't like messing with compiling from source/uninstalling from source.

Install the package 'checkinstall'

$ sudo apt-get install checkinstall

After extracting the .tar.gz, go to its folder and simply do as you would from source except for the last step:

$ ./configure
$ make
$ sudo checkinstall

This will install the program, make a deb package, and make it so that you can easily uninstall it using apt-get remove.

---

### Post by NinjaBunny on 2010-02-04
> **ubuntuman001 said:**
> ...simply do as you would from source....

eh....what?

---

