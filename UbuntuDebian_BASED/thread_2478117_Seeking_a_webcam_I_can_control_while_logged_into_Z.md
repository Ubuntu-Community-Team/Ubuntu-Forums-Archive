---
title: "Seeking a webcam I can control while logged into Zoom"
date: 2022-08-17
forum: Ubuntu/Debian BASED
---

### Post by andy31422 on 2022-08-17
I'm looking for a webcam that I can control while logged into Zoom ie I can adjust pan, tilt, color rendering etc while logged into Zoom. I'm currently using a Logitech c 920 on Antix. I can control it, but only by using a camera widget first, then logging into Zoom. If I need to adjust further I have to log out of Zoom, use the widget, then log back into Zoom and this isn't viable for work meetings.

You probably ask, if I am using Antix, why am I posting in the Ubuntu forum? You have a good point.  My strategy is first, find a camera that works. Ubuntu has a vast user base who are likely to know this. Then try it on Antix. If it doesn't work with Antix, I'll change over to using Ubuntu. The old laptop in question will struggle doing heavy work with Ubuntu, but all I nowadays use it for is Zoom meetings and it should be OK.

Many thanks

Andy3142
Bristol UK

---

### Post by TheFu on 2022-08-17
I've never used zoom, but have a C920 and can use v4l2-ctl (with options) to directly control the webcam.  It isn't a GUI.

For example, to zoom 200%:
```
$ v4l2-ctl -d /dev/video0 -c zoom_absolute=200
```
It would be a fairly small script to make a little menu to choose pre-created settings.

whiptail is one menu system. [according to the manpage whiptail - display dialog boxes from shell scripts]
It isn't hard to make one in pure bash either.

There are heavier GUI methods, like Tk, but the functionality really isn't THAT much better than a TUI like whiptail, IMHO.  By the time I run the program, fine the mouse, point it at the selection and click "Ok", I could have just run a bash alias with everyone already handled.

---

### Post by andy31422 on 2022-08-17
I'm not sure we're talking about the same thing. I'm talking about Zoom online meeting software. 

v4l2-ctl is one of the control widgets I was talking about. It does indeed control the webcam, UNTIL the Zoom meeting starts. At that point Zoom somehow takes control of the webcam away from v4l2-ctl, and it stops working. So to change eg the color rendering, I have to leave the Zoom meeting and quit the Zoom app. Then v4l2-ctl works again and I can adjust the camera, then I have to re-start the Zoom meeting. What I cannot do is to control the camera simultaneously with being in the Zoom meeting.

---

### Post by howefield on 2022-08-17
Thread moved to the "*Ubuntu/Debian BASED*" forum.

---

### Post by TheFu on 2022-08-17
> **andy31422 said:**
> I'm not sure we're talking about the same thing. I'm talking about Zoom online meeting software. 

v4l2-ctl is one of the control widgets I was talking about. It does indeed control the webcam, UNTIL the Zoom meeting starts. At that point Zoom somehow takes control of the webcam away from v4l2-ctl, and it stops working. So to change eg the color rendering, I have to leave the Zoom meeting and quit the Zoom app. Then v4l2-ctl works again and I can adjust the camera, then I have to re-start the Zoom meeting. What I cannot do is to control the camera simultaneously with being in the Zoom meeting.

We were talking about the same thing.  Looks like a Zoom issue, since I use v4l2-ctl with other video conf tools fine.  Glad we don't use Zoom, if they lock the hardware to exclusive use.

---

### Post by andy31422 on 2022-08-17
Thank you. That's a bit depressing. The Zoom forums are no use for this kind of thing.

---

### Post by TheFu on 2022-08-17
[https://community.zoom.com/t5/Meetings/Zoom-ignores-Logitech-LogiTune-camera-settings/td-p/35625](https://community.zoom.com/t5/Meetings/Zoom-ignores-Logitech-LogiTune-camera-settings/td-p/35625) has some Mac users complaining. Some workarounds offered, but those seem to be Mac specific.  If your computer has enough power, you might be able to setup a complex virtual webcam and have OBS feed anything you like into that virtual webcam, which would be shown by Zoom.

[https://obsproject.com/eu/kb/linux-installation](https://obsproject.com/eu/kb/linux-installation) has a PPA for Ubuntu.
[https://linuxgamecast.com/2021/07/obs-linux-basics-virtual-webcam/](https://linuxgamecast.com/2021/07/obs-linux-basics-virtual-webcam/) 
and
[https://obsproject.com/forum/threads/obs-virtual-cam-on-linux.134849/](https://obsproject.com/forum/threads/obs-virtual-cam-on-linux.134849/)

I tried to set this up in early 2020 and it was just a little harder and unstable for my needs at the time. I haven't looked at it since, but it should be much easier these days.  Looks like the flatpak OBS version doesn't work with the virtual webcam, but the PPA does. Also looks to be much easier these days - 2 packages to be installed. Of course, learning OBS isn't trivial.  It is a live broadcasting muxer, which can handle multiple video and audio input sources and mux the resulting output in real-time.  Think of all the different video inputs your evening news deals with. OBS can do that.

---

### Post by andy31422 on 2022-08-18
That's too technical for my pragmatic needs, though thank you once again. But it's comforting to know I'm not alone with the problem. I think the practical answer for me is to bite the bullet and get a good routine with v4l2-ctl.

---

### Post by TheFu on 2022-08-18
> **andy31422 said:**
> That's too technical for my pragmatic needs, though thank you once again. But it's comforting to know I'm not alone with the problem. I think the practical answer for me is to bite the bullet and get a good routine with v4l2-ctl.

I have a start up script that sets my webcam values, then starts a browser with the URL for the meeting.  Nothing too fancy, just 4 commands total. 3 for the v4l2-ctl and 1 browser startup (I actually run the browser inside a private firejail sandbox to prevent the extra nasties that all WebRTC capable browsers allow).  WebRTC has a bunch of security failures, but that's how all these video conferencing tools work.   

If you'd like to be scared about WebRTC: [https://dzone.com/articles/webrtc-security-vulnerabilities-you-should-know-ab](https://dzone.com/articles/webrtc-security-vulnerabilities-you-should-know-ab) is an overview.

---

