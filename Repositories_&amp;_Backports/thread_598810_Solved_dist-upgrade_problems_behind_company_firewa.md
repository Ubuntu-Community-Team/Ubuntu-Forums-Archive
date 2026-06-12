---
title: "Solved dist-upgrade problems behind company firewall"
date: 2007-10-31
forum: Repositories &amp; Backports
---

### Post by hugoheden on 2007-10-31
Good day all,

I had a problem with upgrading to Feisty to Gutsy and I thought I should share the solution here for future reference.

Everything seemed to go well, but finally the update-manager told me [1] that it failed to fetch two files (of the 1200 it needed). I suspect that this had to do with the virus scanner in my company firewall. Or something like that.

However, for some reason, I could download the two package files (deb-files) using wget. Now, how would I continue? How would I tell update-manager to continue, but using those two deb-files that I had manually downloaded?

(One obvious solution, but a little too "brute" for my taste, would be to download and burn the Gutsy Alternate CD, and then restart the upgrade from the beginning but using the CD. That was fortunately not needed.)

The solution was rather simple. It basically just involved copying the manually downloaded deb-files to the same location on the filesystem that update-manager had placed all the other gutsy-deb-files, and then just restarting update-manager.

But a small extra step that were not obvious to me was needed -- step 4 below. After update-manager canceled, what did the trick was the following:

0) Close down update-manager

1) Manually download the missing deb-files using wget

2) Make sure those deb-files are not corrupt in any way (though I am not sure how to really do that).

If they are corrupt, I think update-manager will discover that in later steps below, and try to download them again. And the whole problem here was that downloading fails for some reason.

3) $ sudo cp manually_downloaded_debfiles/*.deb /var/cache/apt/archives/

(not sure if that is dangerous)

4) Make sure that no deb-files with the same name as those manually downloaded exist within /var/cache/apt/archives/partial/ .

If such files exist there, they are likely to be corrupt (half-downloaded or whatever). Update-manager will discover the files under /var/cache/apt/archives/partial/ in later steps, and *remove* the corresponding files in /var/cache/apt/archives/ that were copied in step 3, and try to download them again.

What I did was (not sure if this is dangerous)

$ sudo rm /var/cache/apt/archives/partial/*.deb

5) Re-run update-manager. Everything works.

Many many thanks to Wulfmann, Derek, David and NoOp on the
ubuntu-users mailing list for all the pointers.


-- 
Hugo Heden


[1] "Could not download the upgrades. The upgrade aborts now. Please
check your internet connection or installation media and try again. "

---

