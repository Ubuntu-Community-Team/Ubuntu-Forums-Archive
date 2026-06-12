---
title: "new to servers - is ubuntu server the right tool?"
date: 2011-04-23
forum: Server Platforms
---

### Post by sagesparrow on 2011-04-23
I've been using linux (ubuntu years ago) for some years, but never dealt with setting up servers so I know next to nothing about this subject.

My need is pretty limited and simple.  The server will be solely for allowing access to audio and video files for between 50-100 clients over an LAN.  I do not need or want access to the server from the internet or vice versa (except for updates and upgrades).  I don't want the clients to be able to copy the files to their computers (or at least not easily - of course, anyone with a bit of determination and knowledge could probably do it anyway - that's understood.)  The videos/audios should be able to be played by many people  at once, starting when they want rather than watching a streaming video/audio.  There should be a simple GUI, easy maintenance,etc.

What is the right "tool" for this job?  Ubuntu Server?  If yes, what is the best guide for simple setup and explanation?  What are the hardware requirements for this server?  Other considerations?

If no, can someone point me in the right direction for proper information and software for this job? 

Thanks.

---

### Post by usatonycuba on 2011-04-23
Install apache server, create a website and put links to all your music and video files with the option to playback online ... limiting access to your website, only from your internal network IPs / LAN.?

**PD**:streaming video and audio will consume far too much resources from your server machine, consider a server capable of doing it, and good Sever machine can be a HP ProLiant ML350 G6.. Double  processor and at less 12 GB of RAM. I guess it will do for 100 Clients..?

---

### Post by augustuen on 2011-04-23
Ubuntu Server is a great server platform, I've used it on several servers and I absolutely love it. What you are requesting should be easy to do, as stated above, you could set up an Apache2 server and put all the media files in there, but you could also use Mediatomb, which will set it all up nicely. There is one problem with your plan and what Ubuntu and servers can do though, and that is that you don't want your users to be able to copy the files to their computers. The only way that you could acomplish this is by using a media player created in Flash, and then have that load the files and play them back. This is not a limitation in Ubuntu, but instead a "limitation" on servers in general.

---

### Post by perspectoff on 2011-04-23
Hardware requirements depend on the number of files to be streamed at once.

If this is only for personal use, minimal hardware is needed (especially if using an efficient server version).

If your 50-100 clients will all be accessing things at the same time, though, you shouldn't skimp on hardware.

Apache2 doesn't require many resources, and you can set up WebDAV through Apache2 (or you can use FTP or other filesharing mechanism -- none require much overhead). 

It is the bandwidth of your Internet connection that will be the limiting factor, especially if you have 50-100 simultaneous clients. You need a pretty big pipe for that.

You don't need a server edition to setup a server, though. You can set up the server software on a Desktop edition quite easily. 

The server edition now exists mostly for those who intend to streamline their operation for maximum efficiency (which requires a considerable learning curve for newbies), and does not have a GUI interface for that reason. 

For newbies, I recommend sticking with a desktop edition and just install the server packages on it. You'll be happier with the GUI interface.

Still, a 50-100 user server edition will offer much better efficiency. Just realize that once you add a GUI, the timing is different and it loses some efficiency.

---

### Post by sagesparrow on 2011-04-23
> **augustuen said:**
>  There is one problem with your plan and what Ubuntu and servers can do though, and that is that you don't want your users to be able to copy the files to their computers. The only way that you could acomplish this is by using a media player created in Flash, and then have that load the files and play them back. 

Could you please elaborate on this?  What media players would fit this bill and what audio and video formats?  .flv?  others?

---

