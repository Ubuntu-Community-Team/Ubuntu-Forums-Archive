---
title: "Firefox Reader View"
date: 2015-07-25
forum: Ubuntu, Linux and OS Chat
---

### Post by vasa1 on 2015-07-25
Has anyone tried out Reader View which is now included in Firefox?

I find it a bit unpredictable. When I view a question with a few answers on Ask Ubuntu in Reader View, I find that the question may be missing or that not all the answers on the page are visible.

Then there's this page: [http://webgnuru.com/linux/rsync_incremental.php](http://webgnuru.com/linux/rsync_incremental.php). From there, here's a bit in Reader View:>  We can now use the stat command to examine the properties of that file. Run:

The output will show the inode number and the number of links to the inode. Now, lets create a hard link to foo.txt using the ln command:

Now run stat on each filename. You will see that the output is exactly the same; they share the same inode number and have an equal number of links. You can also use ls -i to view just the inode number; foo.txt and bar.txt are the same thing. And here's the same bit in regular view:>  We can now use the stat command to examine the properties of that file. Run:

    stat foo.txt

The output will show the inode number and the number of links to the inode. Now, lets create a hard link to foo.txt using the ln command:

    ln foo.txt bar.txt

Now run stat on each filename. You will see that the output is exactly the same; they share the same inode number and have an equal number of links. You can also use ls -i to view just the inode number; foo.txt and bar.txt are the same thing.

---

### Post by mystics on 2015-07-25
I'm still trying to always remember that I have the option to use it. I like it for reading articles, but I often forget that it is even there. That isn't really a complaint, though. It isn't like I want them to push it in our faces. I just wish I was better at remembering that there's this new feature I want to use.

---

### Post by vasa1 on 2015-07-25
The list of bugs pulled up by searching for "reader view" is here: [https://bugzilla.mozilla.org/buglist.cgi?quicksearch=%22reader+view%22](https://bugzilla.mozilla.org/buglist.cgi?quicksearch=%22reader+view%22)

The Ask Ubuntu issue occurs on other Stack Exchange pages as well:
[https://github.com/mozilla/readability/issues/232](https://github.com/mozilla/readability/issues/232)

The bugs below deal with other sites (although on the Android platform):
[https://bugzilla.mozilla.org/show_bug.cgi?id=892922](https://bugzilla.mozilla.org/show_bug.cgi?id=892922)
[https://bugzilla.mozilla.org/show_bug.cgi?id=952775](https://bugzilla.mozilla.org/show_bug.cgi?id=952775)

My take is that it's a bit early to rely on Reader View (as incorporated into Firefox) so I'll just disable it once again which is a pity because the concept is appealing.

---

### Post by vasa1 on 2015-08-28
[Firefox/Iceweasel reader mode: How to change the font families]("http://crunchbang.org/forums/viewtopic.php?id=39919")

---

### Post by night_sky2 on 2015-08-29
I've disabled the feature as soon as it was released on Firefox stable.

It's useful for a tablet or smartphone but a desktop computer? Not at all to me. I can read webpages perflectly fine and if needed I can zoom them.

Firefox takes already enough memory as it is, I don't need more bloat. That as well as Pocket and Firefox Hello have been turned off on my PC.

---

