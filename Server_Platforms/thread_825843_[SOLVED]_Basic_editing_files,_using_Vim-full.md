---
title: "[SOLVED] Basic editing files, using Vim-full"
date: 2008-06-11
forum: Server Platforms
---

### Post by Kolipoki on 2008-06-11
I am following the guide in [http://www.howtoforge.com/perfect-server-ubuntu8.04-lts](http://www.howtoforge.com/perfect-server-ubuntu8.04-lts) , where vim-full is installed within the root user for editing. 

Now, the problem is that when I run vi to edit a file, it does open the content, but can't alter it.

Googled and searched in forum here, but only found a reference guide, which still looks somewhat incomprehensible to me, since it seems to need previous combinations of key strokes to edit, differently from the straight forward way you do in a common text editor.

So how do you edit in vim-full? Is there another tutorial for using this editor, or is there any other easier editor that can be used without risking the installation guide on Howtoforge.com?.

Thanks in advance for any help.

---

### Post by mbeach on 2008-06-11
it might be a file permissions issue.

if you "vi somefile"

and the editor launches, and at the bottom it says
"somefile" [readonly]

then likely you don't have rights to edit that file.

instead if you use:
sudo vi somefile
you will be able to edit after you enter your password.  
[see 
[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)
for discussion on sudo if necessary]

there are several tutorials out there on how to use vi, but once you get the 'mode' you are in (edit or command) then things go pretty smooth and slowly you learn the ins and outs of this little dandy.

without trying to be comprehensive:

sudo vi somefile
use your pgup pgdn and arrow keys to get to the area of the file you want to change.
use the 'i' key to start inserting, when complete hit escape to stop inserting, go somewhere else you need a change, hit i again, change what needs changing, then 
:wq  
which will tell the vi that you want to **w**rite changes and **q**uit.  If you want to quit without making changes (because vi apparently went crazy on you) then
:q! 
will **q**uit without writing the changes.

---

### Post by mbeach on 2008-06-11
and a decent intro to vi:
[http://www.washington.edu/computing/unix/vi.html](http://www.washington.edu/computing/unix/vi.html)

---

### Post by Kolipoki on 2008-06-11
> **mbeach said:**
> it might be a file permissions issue.

if you "vi somefile"

and the editor launches, and at the bottom it says
"somefile" [readonly]

I got root access, following this specific guide mentioned in my initial post. It's just that it's the first time I encounter this editor and didn't know (nor found) the commands to make it work.

Thanks a ton Mbeach, you posted exactly what I needed, and much more... *thumbs up

---

