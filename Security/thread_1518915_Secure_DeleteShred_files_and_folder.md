---
title: "Secure Delete/Shred files and folder"
date: 2010-06-27
forum: Security
---

### Post by milca on 2010-06-27
I don't  use the Trash bin because it does not really delete things,speaking from a security point .                                                                          Instead, I gotten used to 'shred' and 'secure-delete' . 
But to move around files, cut-n-paste is very handy.
And I was wandering if items from the Clip get stored somewhere ?
i realize that they get overwritten again and again  in the clipboard but do they also get stored somewhere else?

---

### Post by HermanAB on 2010-06-27
Hmmm, stop playing and encrypt your system.

---

### Post by mkvnmtr on 2010-06-28
I also use secure-delete. I would have to write down a password that is secure so I do not encrypt. Anything you do will be in your home. If you feel you do not wish to leave your work on the computer a trip through the hidden files in home will be worth your time. Anything you do on the clipboard will be there. Do not forget afill once in a while.

---

### Post by cdenley on 2010-06-28
Copy and pasting files would not copy any data from the files to your clipboard. Perhaps just the path to the file. I agree that the best way to protect sensitive data is to use encryption.

---

### Post by milca on 2010-06-29
An explanation : I keep several sensitive files in an encrypted folder. And I needed one file for next day at work. So I mounted the Truecrypt folder , made a copy of the file, drag-n-dropped the copy-file into another folder in an USB stick .   No problems dismounting the folder on the stick. But it did not let me dismount the folder on the hard disk(I must have done something wrong). So without thinking too much, I cut/paste all files into a new unencrypted folder on the Desktop. 
And after restarting computer, TrueCrypt was working fine and had an empty folder  into which I drag-n-dropped all files from the unencrypted folder on the Desktop. After that,  TrueCrypt let me dismount with no problem.
But with all that playing around I started wandering what was left on the hard drive  (usually I just 'copy' but this time I also 'cut/paste '. )

In the hidden folder in Home , I found the Trash sub-folder  and somewhere else some old emails of mine - I believe that I was composing/editing and saving - nothing terrible!.

I will do  ' sfill '  .   Any other suggestions ?
Thanks

---

### Post by cdenley on 2010-06-29
When you move or copy a file from an encrypted filesystem to an unencrypted one, it obviously will write an unencrypted copy. If you overwrite all the data for the file before deletion, you should be fine as long as your filesystem isn't journaling any data.

---

### Post by milca on 2010-06-29
It seems that I get contradictory opinions. So let me make a few statements or  Hypotheses :
-  Highlighting/copying a file and pasting it somewhere else  leaves a trace only in the Clipboard
-  Copying and dragging a file somewhere else leaves a trace only in the Clipboard.
- The clipboard gets overwritten many times and it becomes impossible to figure what was there.

Of course I mean no harm, but I challenge anyone to show where the info from the clip is stored on the hard drive if they believe that. Opinions and common sense thoughts are of course crucial in all human   endeavours but concretely speaking where is the info stored if it is indeed stored,  aside from 2 places : the original file and the 2nd file..

And thank you for putting up with me  (LOL!)

---

### Post by cdenley on 2010-06-29
When you "copy" (ctrl+v) or cut a file in nautilus, it does NOT copy the data from the file to the clipboard. This would be horribly inefficient, especially when copy+pasting large files that don't fit in memory. It would take as long to copy as it does to paste. When you copy or cut in nautilus, it writes the path to the file to memory, so that when you paste the file somewhere, nautilus knows where you are copying/moving the file from.

Try this. Open nautilus. Copy a file. Open gedit (text editor). Paste. You don't paste the data from the file you copied. You paste the path to the file.

---

### Post by milca on 2010-07-01
Things can be put in a different way:  When using  'shred' or 'srm' ,  the contents of a file or folder is completely gone, and only the command remains in this file : ' .bash_history' .

However when one  copy/pastes   or cut/pastes  a file,  does the content of such file  remain in memory even if the file is shredded?

Similarly, when using Sticky Notes and  copying  or cut/pasting  the text into a file which is kept in an encrypted folder,   the question is :  by copying or cutting the text, does it also store in memory?

And also, if a .pdf file is downloaded  and moved somewhere else or opened , will the content be stored automatically in memory?

It looks that there will be a lot of  'sfill sswap sdmem ' to do -  hard on the hd even if no 38 'special ' passes are made (I understand that Gutmann's theory has never been duplicated though it continues to be widely  accepted for a dozen years by now).

---

### Post by HermanAB on 2010-07-04
Howdy,

I can tell you how the military does it.  Then you can decide for yourself how paranoid you want to be.

For Windows systems: Do 'whole disk encryption' using AES156.
For Linux systems: Encrypt /home, /tmp and /swap and wherever else data is stored. Optionally do 'whole disk' encryption.

Media may never be re-used for data at a lower classification.  Media, including hard disks are shredded when broken.

---

### Post by Jimtheplanner on 2010-07-04
Hi Folks,

You can try "Bleach Bit"... I use it to clean out my system not so much for security - cause I'm encrypted, but more for just general house keeping.

It has a shredder ;)

Jim

---

