---
title: "PROC Command Not working"
date: 2014-08-05
forum: Security
---

### Post by firas2 on 2014-08-05
Good Day 

So it looks like I am falling in Love with Linux ,,  so I went out and Bought me a Good Book  

and I tried the PROC command  it showed me access denied  

then I went as root put in the command   asked me for password  and then   nothing showed up did this mean it went through ??

if not why am i getting access denied   ??  and how to prevent this from happing in the future ??

thank u 

here is the cod  /  command 

[IMG]http://i62.tinypic.com/9h7tsg.jpg[/IMG]

---

### Post by mooreted on 2014-08-05
What kind of book are you using? "proc" is not a command, it's a file tree:

[http://en.wikipedia.org/wiki/Procfs](http://en.wikipedia.org/wiki/Procfs)

You would have to use the "sudo" command because users are not allowed access to the operating system, and for good reason. This protects from users messing up the system and hackers exploiting the system.

What your command just did is to add the number "1" to the file "/proc/sys/net/ipv4/tcp_syncookies"

Also, it looks like you don't have a space after ">"

But, that begs the question: why on earth are you trying to add characters to files in /proc?

---

### Post by firas2 on 2014-08-05
Thank u for ur fast reply      it could be that i missed the space   i will try it again 

why U ask ??  no specific reason  I am just fallowing the book as I read  and this is one of the things he recommended  in this chapter 

I did use Sudo   it did not take it

---

### Post by firas2 on 2014-08-05
> **mooreted said:**
> What kind of book are you using? "proc" is not a command, it's a file tree:

[http://en.wikipedia.org/wiki/Procfs](http://en.wikipedia.org/wiki/Procfs)

You would have to use the "sudo" command because users are not allowed access to the operating system, and for good reason. This protects from users messing up the system and hackers exploiting the system.

What your command just did is to add the number "1" to the file "/proc/sys/net/ipv4/tcp_syncookies"

Also, it looks like you don't have a space after ">"

But, that begs the question: why on earth are you trying to add characters to files in /proc?


Still did not work with space and without space :mad:

[IMG]http://i60.tinypic.com/6i4fp0.jpg[/IMG]

---

### Post by steeldriver on 2014-08-05
The space is irrelevant - the issue is that your sudo applies to the echo **command**, but does not apply to the > redirect **operator**. You can do

```

echo 1 | sudo tee /proc/sys/net/ipv4/tcp_syncookies

```

or

```

sudo sh -c 'echo 1 > /proc/sys/net/ipv4/tcp_syncookies'

```

or

```

sudo -i
echo 1 > /proc/sys/net/ipv4/tcp_syncookies
exit

```

/proc/sys/net/ipv4/tcp_syncookies is just a file - you can see its current contents using 'cat'

```

cat /proc/sys/net/ipv4/tcp_syncookies

```

Note that /proc is a 'dummy' filesystem, so any changes you make will be reset when you reboot. You will probably find that "1" is the default value anyway.

---

### Post by firas2 on 2014-08-05
The first command worked 

I wonder y the book had it backwards 

thanks

---

### Post by mooreted on 2014-08-05
Sorry, forgot about sudo and the pipe operator.

Just be careful that you know why you are doing what you are doing. I suppose in this case you are trying to prevent syn flood attacks which was probably patched in the kernel ages ago, but I could be wrong about that.

---

### Post by vasa1 on 2014-08-05
You still haven't told us which book this is :)

Also, the preferred way to show certain types of information such as that entered or displayed in a terminal is to use the "Wrap [CODE] tags around selected text" which should be visible above the area where you type your question or reply to something. There's really no need to link to an image in such cases.

(Note: the [CODE] tag option isn't visible if you choose **Quick Reply**.)

---

### Post by firas2 on 2014-08-06
> **vasa1 said:**
> You still haven't told us which book this is :)

Also, the preferred way to show certain types of information such as that entered or displayed in a terminal is to use the "Wrap [CODE] tags around selected text" which should be visible above the area where you type your question or reply to something. There's really no need to link to an image in such cases.

(Note: the [CODE] tag option isn't visible if you choose **Quick Reply**.)

The Book is well known    u can get it here 


[http://www.amazon.com/Ubuntu-Unleashed-2014-Edition-Covering/dp/0672336936](http://www.amazon.com/Ubuntu-Unleashed-2014-Edition-Covering/dp/0672336936)

as far as the code tags ,,  will do next time   thanks

Dont really understand ur last Line when u say   /////    no need to  link to am image      is this for security reasons ???   or is it just not favorable to load images here ??

Either way it is just Like what  mooreted said   it is a security this 


by the way u will find that Command line on page 175   ;)

---

### Post by QIII on 2014-08-06
There is no need to link an image because if you paste the code between code tags we can read it.  An image is unnecessary.

Adding an image adds to what must be downloaded, which may be a problem for those who have data restrictions or slow connections.  So you should only add images when they are necessary, and you should not simply paste them.  Please use the attachment functionality for that by clicking the "paperclip" icon above the text entry box.

That will insert a thumbnail that another user can choose to click on to enlarge or not.

For example:


[ATTACH=CONFIG]255287[/ATTACH]

---

### Post by vasa1 on 2014-08-06
> **firas2 said:**
> ...
Dont really understand ur last Line when u say    no need to  link to am image      is this for security reasons ???   or is it just not favorable to load images here ??
...
If you only want to share code, using the code tags is simpler and easier to quote in replies to you. Of course there will be times when nothing can replace the information an image provides. So it's really a personal choice, whatever you find more convenient.

Just to be clear, images are welcome and you can use the "Attachments" facility to do so. But note that images uploaded as attachments are visible only to users who are logged in.

Aaargh ... ninja'ed

---

### Post by QIII on 2014-08-06
You were ninja'd slowly, bit by bit.

Took me a while to get that post the way I wanted it!  :)

---

### Post by firas2 on 2014-08-06
will do  thanks    maybe it is a very bad habit  i have learned from other forums and no one has told me otherwise 

many thanks

---

