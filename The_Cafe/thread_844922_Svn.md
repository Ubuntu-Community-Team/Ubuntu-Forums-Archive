---
title: "Svn"
date: 2008-06-30
forum: The Cafe
---

### Post by Riffer on 2008-06-30
Ok I've seen apps that are in a SVN format that I would like to try.  But I know nothing about SVN and how to go about using/installing it.  Can someone give me the simplified explanation?

---

### Post by FranMichaels on 2008-06-30
svn *format*? 
Not SVN (subversion repository)?
[http://en.wikipedia.org/wiki/Subversion_(software)](http://en.wikipedia.org/wiki/Subversion_(software))

If it's the latter, it's same as building from source, it's just instead of downloading release tarballs, you download the code from the svn repository. Then you can download the changes from there and it can be done with a simple command. Also, it is easy to roll back to a previous versions.

make sure you have installed subversion.

svn co someurl name_of_folder

next time to update

svn update

Just build like a normal app (the usual ./autogen.sh && ./configure && make) There should be tutorials on that here at the forums.

P.S. Sorry if this wasn't what you were referring to.

---

### Post by MindFlayer on 2008-06-30
[Here's]("http://ubuntuforums.org/showthread.php?t=51753") a tutorial about installing SVN using Apache.

---

### Post by Riffer on 2008-06-30
> **FranMichaels said:**
> svn *format*? 
Not SVN (subversion repository)?
[http://en.wikipedia.org/wiki/Subversion_(software)](http://en.wikipedia.org/wiki/Subversion_(software))

If it's the latter, it's same as building from source, it's just instead of downloading release tarballs, you download the code from the svn repository. Then you can download the changes from there and it can be done with a simple command. Also, it is easy to roll back to a previous versions.

make sure you have installed subversion.

svn co someurl name_of_folder

next time to update

svn update

Just build like a normal app (the usual ./autogen.sh && ./configure && make) There should be tutorials on that here at the forums.

P.S. Sorry if this wasn't what you were referring to.

Actually yes it is, I'll take another look in the forums for tutorials. thanks

---

