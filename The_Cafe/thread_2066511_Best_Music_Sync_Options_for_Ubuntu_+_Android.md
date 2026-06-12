---
title: "Best Music Sync Options for Ubuntu + Android"
date: 2012-10-04
forum: The Cafe
---

### Post by sajanNOPPIX on 2012-10-04
First of all, this is my first thread here.  Been using Ubuntu exclusively for a while and absolutely love it.  I think desktop Linux is finally getting to a really stable, usable platform for desktops.

All of my servers have used Ubuntu for a while now.
---------

Anyway, what prompted me to register on the forums and open this thread is my frustration with music syncing to my phone.

Banshee and Rythymbox are great, but there doesn't seem to be an awesome all in one solution for Linux yet.

Here's sort of what I want, and am wondering how you guys achieve this.  Don't mind using different software for different steps.

When I buy a track, it goes to my Downloads folder.  I want to open my library manager, browse to and add that track.  I want my library manager to then MOVE that track into my Music folder, creating the Artist and Album folders for me to keep things organized.

/home/sajan/Music/Coldplay/Mylo_Xyloto/Paradise.mp3

I then delete it from my Downloads folder later when I want.

Then in my library I want to be able to create playlists.  I then want a good way to sync my music AND playlists to my Android phone.  I currently use the doubleTwist player, but don't mind switching/buying a different app.

What's the best solution?  Rythmbox doesn't move my music for me.  Banshee does.  However neither sync playlists for me.  Not that I've found anyway.

Thanks for any input.

---

### Post by doorknob60 on 2012-10-04
I'm not sure about playlists, but Banshee syncs and organizes all my music for me, and has a built in Amazon MP3 store plugin, meaning I can easily sync and handle all my music from Banshee. Although I've never tried to sync playlists, and you want that, so I can't really help with that since I haven't tried it.

---

### Post by sajanNOPPIX on 2012-10-05
That's too bad.  I'm sure someone has a solution.  There's no way everyone here is going without the use of Playlists.

---

### Post by doorknob60 on 2012-10-05
I just created a playlist in Banshee, clicked Sync my entire library, and a "Playlists" folder with a few .m3u files inside it (the playlists) was created on my device. Then, I went into Winamp (my preferred Android music player), and they were there! So, looks like Banshee supports playlists after all, at least for me. I have a Samsung Galaxy Player 4.0 with Android 2.3.5. I store my Music on a MicroSD card (not the internal storage), but Banshee handles the MicroSD the exact same way as it handled it when I used to have it on the internal storage, so that should be no different.

Oh, and I just checked, the playlist shows up on the default Music app that came with it too.

---

### Post by thatguruguy on 2012-10-05
There's always the Ubuntu One [music streaming service]("https://one.ubuntu.com/services/music/"). For $3.99/month, you get 20 G. storage on the cloud, and you can stream to any device (Windows PC, Ubuntu PC, android device, iPhone or iPad) that supports Ubuntu One. It does, indeed, support playlists.

---

### Post by sajanNOPPIX on 2012-10-06
> **doorknob60 said:**
> I just created a playlist in Banshee, clicked Sync my entire library, and a "Playlists" folder with a few .m3u files inside it (the playlists) was created on my device. Then, I went into Winamp (my preferred Android music player), and they were there! So, looks like Banshee supports playlists after all, at least for me. I have a Samsung Galaxy Player 4.0 with Android 2.3.5. I store my Music on a MicroSD card (not the internal storage), but Banshee handles the MicroSD the exact same way as it handled it when I used to have it on the internal storage, so that should be no different.

Oh, and I just checked, the playlist shows up on the default Music app that came with it too.

Interesting.  Thanks for coming back and posting that.  I'll have to check again whether the .m3u files are being transferred over to my microSD and if my app supports it.  If not, I guess I'll just start using the Winamp player.

Cheers.

---

### Post by kevdog on 2012-10-06
Just wondering if you are running a rooted android phone.  Wouldn't it be very easy to just run rsync on the android phone to sync with the ubuntu computer so the directories and files are synced?  This could be automated through either a cron job or other such means on the phone.  This of course would require your Ubuntu computer is setup as an ssh server and would be available to access remotely.

---

### Post by sajanNOPPIX on 2012-10-07
> **doorknob60 said:**
> I just created a playlist in Banshee, clicked Sync my entire library, and a "Playlists" folder with a few .m3u files inside it (the playlists) was created on my device. Then, I went into Winamp (my preferred Android music player), and they were there! So, looks like Banshee supports playlists after all, at least for me. I have a Samsung Galaxy Player 4.0 with Android 2.3.5. I store my Music on a MicroSD card (not the internal storage), but Banshee handles the MicroSD the exact same way as it handled it when I used to have it on the internal storage, so that should be no different.

Oh, and I just checked, the playlist shows up on the default Music app that came with it too.

Yeah.  I just tried this and it did the same thing.  m3u files in a Playlists folder.  Which is awesome.  Never noticed that before.

Turns out that doubleTwist doesn't recognize m3u playlists unfortunately.  I guess I'll take a look at Winamp.

Thanks.

---

### Post by sajanNOPPIX on 2012-10-10
> **sajanNOPPIX said:**
> Yeah.  I just tried this and it did the same thing.  m3u files in a Playlists folder.  Which is awesome.  Never noticed that before.

Turns out that doubleTwist doesn't recognize m3u playlists unfortunately.  I guess I'll take a look at Winamp.

Thanks.

Just a quick update in case someone comes across this.  doubleTwist DOES in find find and recognize m3u playlists.  It turns out all I had to do was 'rebuild' the library from the settings menu in the app.

So at the end of the day, my music syncing is all just how I want it using Banshee organize my music files, library, playlists, and properly sync it all to my phone.  AND I still get to use doubleTwist. 

Kudos.

---

### Post by sammyjk on 2013-01-01
I use the built in Rhythmbox player with my Nexus S rooted running 4.2.1. My method: You have to make sure there is at least one mp3 file on the device, in the music folder. RB recognizes it as a 14gb filesystem and a media player, but when I click the media player it gives me a notice that it cannot connect, the 14gb filesystem is still showing though. If you right click on the device the choose sync with library a window pops up with a box at the top, if you click the little subdir arrow you can choose which playlist sync. When you connect the device later it will remember which playlists/songs synced under this menu. It saves all the music in my music folder with dirtree music/artist/album/song while the playlists always appear in my root directory as .pls files. so far the playlists have all been recognized by all my music players (apollo/amazonmp3/aolplay/googleplaymusic/esmediaplayer). Back when I had a win system I was using songbird which getdeb has a version of, I'm not sure how well it works though.

---

### Post by NickGeek on 2013-01-12
> **sammyjk said:**
> I use the built in Rhythmbox player with my Nexus S rooted running 4.2.1. My method: You have to make sure there is at least one mp3 file on the device, in the music folder. RB recognizes it as a 14gb filesystem and a media player, but when I click the media player it gives me a notice that it cannot connect, the 14gb filesystem is still showing though. If you right click on the device the choose sync with library a window pops up with a box at the top, if you click the little subdir arrow you can choose which playlist sync. When you connect the device later it will remember which playlists/songs synced under this menu. It saves all the music in my music folder with dirtree music/artist/album/song while the playlists always appear in my root directory as .pls files. so far the playlists have all been recognized by all my music players (apollo/amazonmp3/aolplay/googleplaymusic/esmediaplayer). Back when I had a win system I was using songbird which getdeb has a version of, I'm not sure how well it works though.

I've noticed this with my Galaxy Nexus, I think it is a problem with MTP support in Ubuntu. With regard to the question I sync my Galaxy Nexus with Synx which doesn't work great but it gets the job done.

---

