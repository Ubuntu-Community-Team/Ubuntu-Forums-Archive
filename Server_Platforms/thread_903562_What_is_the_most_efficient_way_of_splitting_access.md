---
title: "What is the most efficient way of splitting access between customers?"
date: 2008-08-28
forum: Server Platforms
---

### Post by KolosoK on 2008-08-28
Hello,

I finally finished setting up an Ubuntu (8.04) server at work. It's running Samba and a few other things that the company needs. The management is asking if there is any way to share files with the company's customers through FTP or any similar means.

The said files are quotes and such. I would like them to be accessible only by the company that they are meant for. Would I be able to run an Apache server and then create a simple PHP interface that would allow the customers to download files after they enter a password that we give to their particular company? Is there a more efficient way?

---

### Post by de0xyrib0se on 2008-08-28
I would say that is the most efficient and user friendly way, i was faced with the same problem a few months back and believe me most users would be completely lost if you tell them they need to use something different than a browser.

---

### Post by KolosoK on 2008-08-28
> **de0xyrib0se said:**
> I would say that is the most efficient and user friendly way, i was faced with the same problem a few months back and believe me most users would be completely lost if you tell them they need to use something different than a browser.

Yeah, that's what I figured. I am also leaving/quitting soon (I am on an internship), so I have to set it up so our administrator (who doesn't know much about linux) is able to use the system with minimal help from me.

Are there any good free tools available to achieve this, or would I have to script everything from scratch? I know a bit of CSS and JavaScript, but my PHP knowledge is limited.


EDIT: Here's exactly what I'm trying to do:


1) Customer visits "web-site".
2) Customer gets prompted to enter a job number.
3) Depending on the job number entered, customer is taken to the correct location for downloading quotes, reports, etc.

---

### Post by de0xyrib0se on 2008-08-28
Unfortunately I'm not aware of any tools to acomplish this, I coded the whole app in PHP, it worked out quite nicely as its like a virtual file system with permissions and so on, I'd love to give you the code but it was for my employer and they hold the rights over the code.

To give you some pointers, the major problem is how to organize the filesystem in a way you can parse and display in PHP, whether you name the folders by job number or by group id or whatever the case might be.

In my case I opted for storing all my files in a single folder and i have a database structure that says which file falls in which virtual folder, then the user sees a listing of virtual folders but its only for ease of reading behind the scenes everything falls in one folder.

---

### Post by KolosoK on 2008-08-28
> **de0xyrib0se said:**
> Stuff

Ah, so you didn't simply use a ready-made package and configured it. Thank you for the help! I guess I have to read up on some PHP :)

---

### Post by HermanAB on 2008-08-28
Docman: [http://sourceforge.net/projects/docman/](http://sourceforge.net/projects/docman/)

or OWL: [http://sourceforge.net/projects/owl/](http://sourceforge.net/projects/owl/)

For security, use Apache SSL.

Cheers,

H.

---

### Post by de0xyrib0se on 2008-08-28
Although I don't disagree each of these packages are good neither of them covered my requirements, they are both geared towards document management not creating custom document listings per a specific user or case id.

But dont take my word for it you can always play with them.

---

### Post by skunkbad on 2008-08-28
> **KolosoK said:**
> Here's exactly what I'm trying to do:


1) Customer visits "web-site".
2) Customer gets prompted to enter a job number.
3) Depending on the job number entered, customer is taken to the correct location for downloading quotes, reports, etc.

You really ought to require some sort of authentication. Apache allows for some simple authentication using .htpasswd files, and while not 100% secure, you would eliminate the chance of sombody guessing job numbers to view other people's documents. If you put each customer's docs in a separate folder, along with it's own .htpasswd file for authentication, you would simply send links to the customer with their login name and password. I don't think it gets any easier than that.

---

### Post by KolosoK on 2008-08-28
> **skunkbad said:**
> You really ought to require some sort of authentication. Apache allows for some simple authentication using .htpasswd files, and while not 100% secure, you would eliminate the chance of sombody guessing job numbers to view other people's documents. If you put each customer's docs in a separate folder, along with it's own .htpasswd file for authentication, you would simply send links to the customer with their login name and password. I don't think it gets any easier than that.

That sounds pretty interesting. We don't really mind people guessing job numbers, as they are 6+ digits and don't go in order. However, can your idea be set up to be used with a web interface? If so, could you point me in the correct direction?

---

### Post by rlanham on 2008-08-29
Why not just use Proftpd or other FTP variant with SSL and store the login/password and user path in a MySQL database. Doesn't get much easier to add a new user then firing up a DB editor or phpMyAdmin. Here is a good howto:

[http://howtoforge.com/virtual-hosting-with-proftpd-and-mysql-ubuntu-8.04](http://howtoforge.com/virtual-hosting-with-proftpd-and-mysql-ubuntu-8.04)

---

### Post by KolosoK on 2008-08-29
That's actually how I was going about it originally. However, I have no experience with MySQL. Also, we have many customers who would not be able to figure out how to use the FTP system :( I might give it a try if the Apache/PHP solution will not work.

EDIT: The real problem is that the other administrator here will not be able to figure out how to add users later on.

EDIT 2: Alright, going to try passwording each individual folder the way someone mentioned in this thread.

---

### Post by yoman on 2008-08-29
[http://sikh.myminicity.com/](http://sikh.myminicity.com/)

---

