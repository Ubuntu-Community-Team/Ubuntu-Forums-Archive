---
title: "Dealing with code efficiently"
date: 2011-07-10
forum: The Cafe
---

### Post by rmcellig on 2011-07-10
I am not sure if this is the right forum to post this (please advise), but here is my problem. On my Mac, I use Text wrangler to store all of my html and css code I use to create my web site. So far so good, or should I say so great because I love using Textwrangler. My problem is that when I am aay from my computer or on another computer with another OS, I can't use Textwrangler. I am looking for a way (and I hope this is possible), to store and edit my code online no matter where I am or what computer I am using.

Is this do-able? Maybe a free solution?

---

### Post by forrestcupp on 2011-07-10
If you're using Mac and Windows computers, you can install DropBox. I don't know that they have it for Linux. It creates a folder on your computers that the software automatically syncs with its server. You get 2GB for free. You can drag files to your DropBox folder, just like you normally would to a local folder, and the software automatically uploads it to the same folder on your account on their server without you even knowing it. You can set it up on multiple computers and share the folder on them. Other than the extra time it takes to download and upload, it's exactly like working with your files locally.

---

### Post by rmcellig on 2011-07-10
I use Dropbox all the time and love it!!

Because I have my code in Textwrangler saved as HTML files, do I need textwrangler to open those or will any text editor in any is open those files for editing?

How can I open those HTML files for editing if I access my dropbox online?

Like I said, I LOVE using dropbox and if I can stay with dropbox that would be fantastic!! Let me know what my options are.

---

### Post by Bandit on 2011-07-10
> **rmcellig said:**
> I use Dropbox all the time and love it!!

Because I have my code in Textwrangler saved as HTML files, do I need textwrangler to open those or will any text editor in any is open those files for editing?

How can I open those HTML files for editing if I access my dropbox online?

Like I said, I LOVE using dropbox and if I can stay with dropbox that would be fantastic!! Let me know what my options are.

They are just text files, you can open them in Notepad or any other text editing program. The only real issue that you will run into is lack of syntax highlighting and slightly jacked up formatting (spacing mostly).

---

### Post by juancarlospaco on 2011-07-10
I use Ubuntu One and Bazaar/Launchpad at the same time.

---

### Post by CharlesA on 2011-07-10
Any text editor can open them. They are just text. :)

Also +1 to dropbox.

---

### Post by psusi on 2011-07-10
What exactly does this "text wrangler" do?

---

### Post by CharlesA on 2011-07-11
> **psusi said:**
> What exactly does this "text wrangler" do?

It looks to be just a text editor.

If I'm coding, I use Bluefish, but that's just me. :p

---

### Post by CraigPaleo on 2011-07-11
> **rmcellig said:**
> I use Dropbox all the time and love it!!

Because I have my code in Textwrangler saved as HTML files, do I need textwrangler to open those or will any text editor in any is open those files for editing?

How can I open those HTML files for editing if I access my dropbox online?

Like I said, I LOVE using dropbox and if I can stay with dropbox that would be fantastic!! Let me know what my options are.

Then use dropbox. There's a deb for it. [http://www.dropbox.com/downloading?os=lnx](http://www.dropbox.com/downloading?os=lnx)
> 
How does it work?

The installer (deb file) will perform the following actions:

    Install the open-source Dropbox plug-in for the Nautilus File Manager
    Adds Dropbox to your default repository for automatic upgrades.
    Downloads and installs the Dropbox binary.

It'll bring up the Software Center. Once it's installed, it'll prompt you to restart Nautilus. Click 'restart' and then 'next." It'll install dropbox.

---

### Post by el_koraco on 2011-07-11
> **psusi said:**
> What exactly does this "text wrangler" do?

it wrangles text!

---

### Post by ssam on 2011-07-11
i would strongly recommend a revision control system (bazaar, git,...). not only does this let you sync code between multiple machines. it also lets you track and  merge changes.

---

### Post by Erik1984 on 2011-07-11
> **el_koraco said:**
> it wrangles text!

Had to look that up:

```

–verb (used with object) 2.to argue or dispute.

3.to tend or round up (cattle, horses, or other livestock).

4.to obtain, often by contrivance or scheming; wangle: He wrangled a job through a friend.

```[http://dictionary.reference.com/browse/wrangle](http://dictionary.reference.com/browse/wrangle)

I guess .3 is the most accurate meaning in this context.

---

### Post by rmcellig on 2011-07-11
Thanks for all the suggestions but I think my main concern is that when I am away from my computers and need to use another computer can I go to the dropbox website locate the file I want to look at/ edit open the file edit it will it save back to my dropbox file or do I have to save the file elsewhere and upload it to my dropbox folder?

---

### Post by grahammechanical on 2011-07-11
HTML and CSS are industry standards. Any editor design to create web pages would understand these documents and let you edit them and then save in the same format as HTML or CSS. It does not matter what OS the web editor runs on. 

As a test use your web browser to view the page source of a web page. With Firefox I right click and select View page source. I am sure that the web browser on a Mac has a way of doing the same thing. Now you will see all the coding for that web page. You can copy and paste the page contents into your own web page editor (Text wrangler) and you will be able to edit it even though that page might not have been created by text wrangler but by some other editor.

Be assured that you can edit HTML and CSS files on different operating systems and with different editors and there will not be any difference to using only one program to do the editing.

Regards.

---

### Post by Bandit on 2011-07-11
> **CharlesA said:**
> It looks to be just a text editor.

If I'm coding, I use Bluefish, but that's just me. :p

Yea Bluefish is excellent.

---

### Post by Random_Dude on 2011-07-11
> **forrestcupp said:**
> If you're using Mac and Windows computers, you can install DropBox. I don't know that they have it for Linux. 

There is a linux version of dropbox. Works very well.

Cheers :cool:

---

### Post by rmcellig on 2011-07-11
Thanks for the comments on using different editors.

---

### Post by forrestcupp on 2011-07-11
I agree with everyone else that there are plenty of text/code editors you can use that will work on any platform.

> **CraigPaleo said:**
> Then use dropbox. There's a deb for it. [http://www.dropbox.com/downloading?os=lnx](http://www.dropbox.com/downloading?os=lnx)Awesome. I didn't know they had a Linux version. I'll have to install that on my Mint partition.

> **rmcellig said:**
> Thanks for all the suggestions but I think my main concern is that when I am away from my computers and need to use another computer can I go to the dropbox website locate the file I want to look at/ edit open the file edit it will it save back to my dropbox file or do I have to save the file elsewhere and upload it to my dropbox folder?You can install dropbox on any of your computers, link it to your account, and use it like a local folder and save html files directly from your text editor to that folder. But if you're on a public computer that you're not allowed to install dropbox onto, then you'll have to save your file locally, then go to the web site and upload it to your dropbox folder. Then you will be able to access it normally from any computer you have dropbox installed on.

Another cool thing about dropbox is that you can create a subfolder that can be shared between multiple accounts. I just created one so that my brother and I can share files whenever we need to.

---

### Post by WRDN on 2011-07-11
> **ssam said:**
> i would strongly recommend a revision control system (bazaar, git,...). not only does this let you sync code between multiple machines. it also lets you track and  merge changes.

+1. I've used Git for a few years now to manage my software development projects, with a personal server. Though there is a slight learning curve, the benefits of using a version control system (in particular, a distributed system) far outweigh the negatives.

It's far from trivial to setup Git on a personal server however, so I would suggest a service such as [Unfuddle]("http://unfuddle.com/"), [ProjectLocker]("http://www.projectlocker.com/") or [GitHub]("https://github.com/").

Note while it can be setup on a server, you can use it locally also, with no network communication.

---

### Post by forrestcupp on 2011-07-11
> **ssam said:**
> i would strongly recommend a revision control system (bazaar, git,...). not only does this let you sync code between multiple machines. it also lets you track and  merge changes.

> **WRDN said:**
> +1. I've used Git for a few years now to manage my software development projects, with a personal server. Though there is a slight learning curve, the benefits of using a version control system (in particular, a distributed system) far outweigh the negatives.
I'd say something like Git is probably a pretty big overkill for some html files that make up a web site.

---

### Post by Dry Lips on 2011-07-11
So, this the thread where we push our dropbox invites?

---

### Post by forrestcupp on 2011-07-11
> **Dry Lips said:**
> So, this the thread where we push our dropbox invites?

I have a whopping 2GB. Will you accept my invitation? :)

---

### Post by CharlesA on 2011-07-11
> **Dry Lips said:**
> So, this the thread where we push our dropbox invites?

That thread would be over [there]("http://ubuntuforums.org/showthread.php?t=1128464"). *points*

---

### Post by Dry Lips on 2011-07-11
> **CharlesA said:**
> That thread would be over [there]("http://ubuntuforums.org/showthread.php?t=1128464"). *points*

Actually I knew about that thread, but thanks anyway! :) I haven't posted
there yet because it seems kind of futile... It seems as if everybody keen 
on having a dropbox account already has one.

---

### Post by CharlesA on 2011-07-11
> **Dry Lips said:**
> Actually I knew about that thread, but thanks anyway! :) I haven't posted
there yet because it seems kind of futile... It seems as if everybody keen 
on having a dropbox account already has one.

Sure seems like it. I posted mine over there, but no bites. :o

---

