---
title: "WoW &quot;There was an error logging in.&quot;"
date: 2010-01-27
forum: Wine
---

### Post by Omeil on 2010-01-27
Hi all,

Since i have updated World of Warcraft to 3.3.0a I have been having issues with logging in, it seems like it does not like the @ in my email address and it does not even try to authenticate. I have tried installing the two runtime packages through wine tricks but i am still receiving this error. Is there any other workaround to this?

"There was an error logging in. Please try again later. If the problem persists, please contact Technical Support at: blah blah blah" is the instant message

Kind Regards,

Omeil

---

### Post by Pikestaff on 2010-01-27
I did a quick google search and found [this]("http://us.blizzard.com/support/article.xml?locale=en_US&articleId=26433&pageNumber=1&searchQuery=realmlist.wtf")... maybe try the realmlist suggestion?

---

### Post by CyDharttha on 2010-03-02
This happened to me as well. First thing I noticed was, today's patch deleted a bunch of files in the Warcraft folder, including Launcher.exe and Repair.exe. The following thread includes these files, uploaded by another user:

[http://forums.worldofwarcraft.com/thread.html?topicId=23425527182&sid=1](http://forums.worldofwarcraft.com/thread.html?topicId=23425527182&sid=1)

That was only the first step, still quite a mess. There were many more files missing from the Warcraft folder (I wasn't immediately aware), and I eventually ran Repair.exe. At the end of the process (10 mins) it downloaded the missing files. I'm up and running. Hope this helps!

---

### Post by twistered on 2010-03-03
A few users who have installed Snow Leopard on their systems,for this reason error may occurred.

---

### Post by Omeil on 2010-03-03
Hi All thanks for the suggestions, but none worked :( i reinstalled wow and it worked!! this time, but then i tried going to northrend now my character is stuck because i keep receiving a critical error thats related to maps. So I have to reinstall wow again -_-. ah just my luck.

---

### Post by mw13068 on 2011-04-18
I was having this "error logging in" problem when I had my World of Warcraft dir stored on a different partition and symlinked into ~/.wine/drive_c/Program Files/

The fix was copying the World of Warcraft directory from a separate partition onto the same partition with my ~/.wine directory.

---

