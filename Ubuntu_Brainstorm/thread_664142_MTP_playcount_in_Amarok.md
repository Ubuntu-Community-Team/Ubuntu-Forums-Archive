---
title: "MTP playcount in Amarok"
date: 2008-01-10
forum: Ubuntu Brainstorm
---

### Post by narehart on 2008-01-10
I need the communities help here.  I want to implement MTP playcount and last.fm submission of tracks in Amarok.  I've browsed a few files and ran Amarok in a terminal but I'm far from experienced at this sort of thing. All I have to offer is this file I found on the Amarok mailing list: 

```

Index: mtpmediadevice.cpp
===================================================================
--- mtpmediadevice.cpp	(revision 683997)
+++ mtpmediadevice.cpp	(working copy)
@@ -65,7 +65,7 @@
     m_playlistItem = 0;
     setDisconnected();
     m_hasMountPoint = false;
-    m_syncStats = false;
+    m_syncStats = true;
     m_transcode = false;
     m_transcodeAlways = false;
     m_transcodeRemove = false;
@@ -1639,6 +1639,9 @@
     this->setFolderId( track->parent_id );
 
     this->setBundle( *bundle );
+
+    this->rating=track->rating;
+    this->usecount=track->usecount;
 }
 
 /**
Index: mtpmediadevice.h
===================================================================
--- mtpmediadevice.h	(revision 683997)
+++ mtpmediadevice.h	(working copy)
@@ -51,10 +51,18 @@
         void                    setFolderId( const uint32_t folder_id ) { m_folder_id = folder_id; }
         void                    readMetaData( LIBMTP_track_t *track );
 
+        // rating and usecount accessors
+        void                    setRating(int new_rating) { rating=new_rating; }
+        int                     getRating() { return rating; }
+        int                     getUsecount() { return usecount; }
+
     private:
         u_int32_t               m_id;
         MetaBundle              m_bundle;
         uint32_t                m_folder_id;
+        // rating and usecount obtained via libmtp
+        uint16_t                rating;
+        uint32_t                usecount;
 };
 
 class MtpPlaylist {
@@ -117,6 +125,18 @@
         MtpPlaylist         *playlist() { return m_playlist; }
         QString             filename() { return m_track->bundle()->url().path(); }
 
+        int                 recentlyPlayed() { return m_track->getUsecount() > 0; } // it has been played if the usecount is greater than zero
+        bool                ratingChanged() { return true; } // i don't think mtp can tell if the rating has changed so just say it is always changed
+        void                setRating(int rating) { m_track->setRating(rating); }
+        int                 rating() { return m_track->getRating(); }
+
+        QDateTime           playTime()
+        {
+            // libmtp can't tell us when a track was played so return an invalid time
+            QDateTime t;
+            return t;
+        }
+
     private:
         MtpTrack            *m_track;
         MtpPlaylist         *m_playlist;

```

So, what do you say guys? Can we do this?

---

### Post by narehart on 2008-01-20
bump

---

### Post by narehart on 2008-01-20
bump!

---

### Post by narehart on 2008-01-20
Well, I've found a program called Zenses for XP that can scrobble tracks played on Zen devices.  I haven't gotten it working with my player yet but I'll continue trying.  Anyways, the program is open source and the developers are planning on making the next version cross platform (OSX, LINUX) but I can't help but think that there has to be some way to get Amarok to do this without installing another program.

I did manage to get Zenses working with my player in a virtual machine.  I've also got the source code if any one is interested.

---

### Post by narehart on 2008-01-22
Okay, I figured out the procedure that would allow for a script that could submit tracks to last.fm.  It would go something like this:

1. handshake the scrobble protocol and get username and password
2. call libmtp to dump track info
3. if playcount is greater than 0 time stamp track(start with current system time and add 15 sec for each usecount) and call scrobble function.
    scrobble function: submit track name, artist, usecount, time
4. reset usecount to 0

I have some idea how to implement this in C++ but I'm definately not skilled enough to put it all together.  Here are some leads:

1. [scrobble protocol page.]("http://www.audioscrobbler.net/development/protocol/")
2. if you download libmtp [here]("http://sourceforge.net/project/downloading.php?groupname=libmtp&filename=libmtp-0.2.4.tar.gz&use_mirror=easynews") and extract it, there is a file in the examples folder called tracks.c.  It has the code for calling libmtp to dump the track info.
3. I suppose to implement the time stamp you make a global varial called time and have it set to current system time (I don't know how to execute this) and then when ever a usecount is detected do time = time + 15 sec.
4. resetting the use count is just a matter of amending the tracks.c file mentiond in number 1:
```
I just added the following function:

static void reset_usecount(LIBMTP_mtpdevice_t *device, LIBMTP_track_t*track)
{
   track->usecount = 0;
   LIBMTP_Update_Track_Metadata(device, track);
 }

 Then down by 'dump_trackinfo(track)' called it:

reset_usecount(iter, track);
```

Well, I hope somebody can take a look at this and tell me if it's possible and help me to get it done.

---

### Post by ashenphoenix on 2008-05-30
I would be totally up for seeing this program, but I can't code, sorry :(

---

### Post by Sense on 2009-03-22
There is a project that's doing this on SF: [http://sourceforge.net/projects/mtp2lastfm/](http://sourceforge.net/projects/mtp2lastfm/)

However, I'm not able to compile it and the pre-compiled version is for 32bit only. Furthermore, it seems to use libmtp7, which was last used in 8.04. So I can't test it. 
Maybe it's of use to you.

---

