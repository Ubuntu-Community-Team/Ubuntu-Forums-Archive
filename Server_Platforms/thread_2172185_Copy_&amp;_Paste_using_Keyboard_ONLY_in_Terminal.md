---
title: "Copy &amp; Paste using Keyboard ONLY in Terminal?"
date: 2013-09-03
forum: Server Platforms
---

### Post by GMHilltop on 2013-09-03
I've installed linux server 12.04 LTS and I have run

> sudo blkid

I want to edit the fstab file so another partition is mounted automatically and I wanted to copy and paste the uuid=XXXXXXXXXXXXXXXXXXXXX

. . . how do I do that without the mouse?

Thanks

---

### Post by alarme on 2013-09-03
Hi:

# first, make a backup
cp /etc/fstab /etc/fstab.bak

# append output of blkid at the end of fstab
sudo blkid >> /etc/fstab

# CAUTION:
#   >>  append
#   >    OVERWRITE - delete original contents of the file begin redirected

# edit fstab
sudo nano /etc/fstab

# in nano:
# ctrl+U  cut
# ctrl+K  paste

Cheers

---

### Post by GMHilltop on 2013-09-03
Thanks alarme. That helps

Learning how to work in terminal is coming slowly, but surely.
I am sort of surprised that there isn't a more graceful way to handle this.

If the output were to be 'Huge' it could hammer in a awful lot of crap at the end of a file when all you want is one line.

So far I've been pleasantly surprised with navigating and the shortcuts (like hitting TAB) in terminal - this is the first thing that I've run into that seem rather archaic.

Is this the ONLY way of dealing with this sort of a situation?

---

### Post by kpothi on 2013-09-04
If you are looking for keyboard shortcuts and if ctrl+c and ctrl+v didn't work for copy & paste, then you may use ctrl+shift+c and ctrl+shift+v to do the same as mentioned in the [help page for working with terminal](https://help.ubuntu.com/community/UsingTheTerminal#Pasting_in_commands).

---

### Post by nerdtron on 2013-09-04
[[COLOR=#000000]GMHilltop[/COLOR]]("http://ubuntuforums.org/member.php?u=1056293") : Be at home in the command line. I recommend this free ebook. Easy to read and follow. [http://www.rigacci.org/docs/biblio/offline/TLCL-09.12.pdf](http://www.rigacci.org/docs/biblio/offline/TLCL-09.12.pdf)

---

### Post by SeijiSensei on 2013-09-04
You can also use Ctrl-K to cut from the cursor position to the end of the line, and Ctrl-Y to retrieve ("yank") the cut text.  These are the same commands used in Emacs and Emacs clones like jed.

---

### Post by GMHilltop on 2013-09-04
Thanks everyone for the help. There simply doesn't seem to be a 'nice' way to do it.

[The second post vyalarme here]("http://ubuntuforums.org/showthread.php?t=2172185&p=12778089#post12778089")[[COLOR=#000000][/COLOR]]("http://ubuntuforums.org/member.php?u=160465") works best for my purposes although the **WARNING IS WELL NOTED** - the difference between ONE   ' **>** '   and   TWO   ' **>>** '   could be disastrous!
Like I said, I'd have thought there would have been a better way to do this by now considering how long linux has been running.  Oh well.

ctrl+v, ctrl+shift+v, etc simply do not work.

I'll just have to get used to the way of copying and pasting with VIM and NANO

Thanks again everyone.

---

### Post by volkswagner on 2013-09-04
Using SSH to connect with a terminal app gives the greatest joy using copy/paste for text console tasks.

---

### Post by GMHilltop on 2013-09-05
Can you use the same method for copying info from one file to another?

In other words:

sudo /etc/my_first_file >> /etc/my_2nd_file

Will that append the data in the first file to the 2nd?

---

### Post by GMHilltop on 2013-09-05
I am not sure what I am doing wrong:

```

sudo blkid>>test_file 
-bash: test_file: Permission denied

```


 I created an empty file with
```

touch test_file

```

Everything is owned by root, what am I missing?
Why is the permission denied?

---

### Post by nerdtron on 2013-09-05
> **GMHilltop said:**
> I am not sure what I am doing wrong:

```

sudo blkid>>test_file 
-bash: test_file: Permission denied

```


 I created an empty file with
```

touch test_file

```

Everything is owned by root, what am I missing?
Why is the permission denied?

I can't reproduce your error? Can you post what you have done including the shell prompt?
Here's what I did.
Created empty file:
```
kenneth@nerdtron:~/sample$ touch test_file

```
List the directory contents and see the permissions, also the size  is zero because it is empty.
```
kenneth@nerdtron:~/sample$ ls -l
total 4
-rw-rw-r-- 1 kenneth kenneth 0 Sep  6 10:18 test_file
```
Append the output of blkid command to test_file
```
kenneth@nerdtron:~/sample$ sudo blkid >> test_file 

```
List the directory contents and see the permissions, it show a size of 312 since the file has now contents.
```
kenneth@nerdtron:~/sample$ ls -l
total 4
-rw-rw-r-- 1 kenneth kenneth 312 Sep  6 10:19 test_file
```
Output the contents of the test_file
```
kenneth@nerdtron:~/sample$ cat test_file
/dev/sda1: UUID="30f6bb2a-6580-45dc-9232-6a56c6457d4b" TYPE="ext4" 
/dev/sda5: UUID="f43e6b1f-822b-401d-a99a-65dad6b1decc" TYPE="swap" 
/dev/sda6: LABEL="bbbeeepppp" UUID="1b5e52b9-9335-4864-9300-32a5f8ab8b3a" TYPE="ext4" 
/dev/sda7: LABEL="bbboooppppp" UUID="3427c05a-911b-4fcf-93c6-97119e42492d" TYPE="ext4" 

```

---

