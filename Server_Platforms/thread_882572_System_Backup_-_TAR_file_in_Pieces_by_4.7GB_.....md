---
title: "System Backup - TAR file in Pieces by 4.7GB ...."
date: 2008-08-07
forum: Server Platforms
---

### Post by stoynev on 2008-08-07
Hello folks, I want to make FULL BackUp on my Mail Server but its almost 20GB of files ....., Thats why I want to make the backup on TAR files in pieces of 4.7GB to write them to DVDs.
Does any one knows a way to do that? Software or .....?
Thanks.

---

### Post by hyper_ch on 2008-08-07
[http://unixhelp.ed.ac.uk/CGI/man-cgi?split](http://unixhelp.ed.ac.uk/CGI/man-cgi?split)

---

### Post by Titan8990 on 2008-08-07
Will that split command also put the archive back together?

---

### Post by hyper_ch on 2008-08-07
dunno... but you can cat them together

---

### Post by Titan8990 on 2008-08-07
Something like this?

tar -xvf file1.tar && file2.tar && file3.tar

---

### Post by Yannick Le Saint kyncani on 2008-08-07
> **stoynev said:**
> Hello folks, I want to make FULL BackUp on my Mail Server but its almost 20GB of files .....

If you have 20GB of text files only, they may be compressed to 10% of their size.

---

### Post by hyper_ch on 2008-08-07
cat newfile_vol_* > newfile.tar

---

### Post by Titan8990 on 2008-08-07
ah, I thought you were saying cat as in short of catenate.

---

### Post by hyper_ch on 2008-08-07
it is ;)

> 
NAME

       cat - concatenate files and print on the standard output


---

### Post by Titan8990 on 2008-08-07
And thats a command I use everyday....


Always good to learn something new.

---

