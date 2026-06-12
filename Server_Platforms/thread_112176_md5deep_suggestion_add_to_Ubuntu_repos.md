---
title: "md5deep suggestion: add to Ubuntu repos?"
date: 2006-01-03
forum: Server Platforms
---

### Post by lotusleaf on 2006-01-03
[color=red]**Update 01-15-2006:**[/color] [color=green]Thanks to Seth, [md5deep is now in the repos for Dapper](http://packages.ubuntu.com/dapper/utils/md5deep).[/color] *Hooray!* :)

[COLOR="DimGray"][**md5deep**](http://md5deep.sourceforge.net/) "is a cross-platform set of programs to compute MD5, SHA-1, SHA-256 Tiger, or Whirlpool message digests on an arbitrary number of files. The programs run on Windows, Linux, *BSD, OS X, Solaris, and should run on most other platforms. md5deep is similar to the md5sum program found in the GNU Coreutils package, but has the following additional features:

    * Recursive operation - md5deep is able to recursive examine an entire directory tree. That is, compute the MD5 for every file in a directory and for every file in every subdirectory.
    * Time estimation - md5deep can produce a time estimate when it's processing very large files.
    * Comparison mode - md5deep can accept a list of known hashes and compare them to a set of input files. The program can display either those input files that match the list of known hashes or those that do not match. Hashes sets can be drawn from the National Software Reference Library, iLook Investigator, Hashkeeper, or md5sum, and other generic hash generating programs. Users are welcome to add functionality to read other formats too!
    * File type mode - md5deep can process only files of a certain type, such as regular files, block devices, etc."[/COLOR]
[color=brown]--------------------------------------------------------------[/color]

I find md5deep and the included tools to be powerful and very useful. It's easy enough to download the source and install, but I think it deserves to be in the repos as it's a quality set of tools. I wasn't quite sure where to post this as it's not fit for the backports forum area since it's not in the repos, so here it went. :) In the past I suggested Rkhunter and magically it appeared in the repos due to someone's kindness so now I'm suggesting md5deep. :) The file manager Krusader [now supports md5deep](http://krusader.sourceforge.net//phpBB/viewtopic.php?t=1024) so those using Krusader would easily be able to use it with Krusader too by quickly and easily downloading a .deb file for md5deep from the repos, should it be added.

Could md5deep be given consideration for adding as a .deb to the repos so everyone may easily find and install it?

Thanks for reading! :)

---

### Post by majikstreet on 2006-01-03
hmhp... /me hopes a motu comes here..

Kyral says add it to [https://wiki.ubuntu.com/UniverseCandidates](https://wiki.ubuntu.com/UniverseCandidates)

---

### Post by Seth on 2006-01-03
I'll give it a go tonight.

By the way, requests normally go here: [https://wiki.ubuntu.com/UniverseCandidates](https://wiki.ubuntu.com/UniverseCandidates)

Most MOTUs do not read the forums.

---

### Post by Seth on 2006-01-03
Success! I've packaged md5deep 1.9.2-0ubuntu1 and added it to the review queue. Please monitor [http://revu.tauware.de/details.py?upid=1378](http://revu.tauware.de/details.py?upid=1378) for details, or to grab the sources and build them yourself.

---

### Post by Seth on 2006-01-06
Hi Lotusleaf,

I've received one "advocate" for my package, so only one more is needed for it to enter Dapper. Look for it this week in Dapper :)

---

### Post by lotusleaf on 2006-01-07
Seth: Once again, thanks for your quick attention and kind responses to my request(s), and the links, I appreciate it! :) I see md5deep has been added for consideration to [Universe Candidates](https://wiki.ubuntu.com/UniverseCandidates), excellent! :) Again, thank you. :) I do read the various Ubuntu mailing list(s) from time to time, though for this type of thing perhaps I should post there in the future.

majikstreet: Thank you for your post and the link. :)

---

### Post by Seth on 2006-01-11
I have uploaded md5deep to Dapper Universe.

[http://lists.ubuntu.com/archives/dapper-changes/2006-January/004574.html](http://lists.ubuntu.com/archives/dapper-changes/2006-January/004574.html)

---

### Post by lotusleaf on 2006-01-15
Wonderful news! Thanks Seth for making [this](http://packages.ubuntu.com/dapper/utils/md5deep) possible, I appreciate your efforts! \\:D/

---

