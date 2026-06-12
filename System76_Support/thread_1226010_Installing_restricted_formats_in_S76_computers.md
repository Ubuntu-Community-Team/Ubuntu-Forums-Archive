---
title: "Installing restricted formats in S76 computers"
date: 2009-07-29
forum: System76 Support
---

### Post by Eldera on 2009-07-29
Please clarify this tutorial:
[http://knowledge76.com/index.php/Installing_Restricted_Formats](http://knowledge76.com/index.php/Installing_Restricted_Formats)

Does one do this:

    * Click Applications &#8594; Add/Remove. In the top right, change the setting to All available applications. Select Other in the left panel and then select the Ubuntu restricted extras package. Click Apply Changes.

And then do this:
    * Open your terminal (Applications > Accessories > Terminal) then copy and paste the following commands into the terminal window. Enter your user password when prompted. 
sudo wget http://www.medibuntu.org/sources.list.d/`lsb_release -cs`.list  --output-document=/etc/apt/sources.list.d/medibuntu.list
sudo apt-get -q update; sudo apt-get --yes -q --allow-unauthenticated install medibuntu-keyring; sudo apt-get -q update

And then do this:
64 Bit Ubuntu Users:
sudo apt-get install libdvdcss2 w64codecs


Or does one do
 * Click Applications &#8594; Add/Remove. etc
OR * Open your terminal (Applications > Accessories > Terminal) then etc
NOT BOTH

Thank you, Eldera

Currently running tri-boot Jaunty 64-bit 2.6.28-13 generic nVidia driver 173

Off topic, but someone is going to wonder what I mean by tri-boot Jaunty. I have three partitions each with Jaunty. One is for programs that I have studied, understand and use frequently at default resolution, Two is for programs I understand but need to adjust for poor eyesight, and Three is for downloading and working with things I am still learning. If/when I mess up on three, I can delete it and start fresh without disturbing all the projects I have on One. It has been suggested I could do this more efficiently with virtualization, but I haven't had time to reseach virtual machines.

---

### Post by ajgreeny on 2009-07-29
You probably need to do both, ie the ubuntu-restricted-extras, and also the various medibuntu packages, as the ubuntu restricted package will not give you the libdvdcss2 which is needed for many commercial DVDs to play.  In my case, I don't bother with the ubuntu restricted extras, but go straight to the medibuntu packages and then add the flash plugin separately, but it may be easier to stick to the recommendations you have, but definitely both parts of it are needed, in my opinion.

Regarding your query on virtualisation, I think it is your choice entirely.  I also run a separate partition with a testing install of ubuntu on it, and I link all my document, photo and music folders, etc etc in to that, rather than keep them separate, so there is no replication of too much in the way of data files.  I find this a good way of dealing with testing various parts of the operating system, and edits to system files I may read about and don't want to edit in my main system, just in case it breaks something.  It it ain't broke, don't fix it.  The trouble is, if you always kept to that rule, you would never try anything new, and I like to test things out.

---

### Post by thomasaaron on 2009-07-29
You do this...

> 
* Click Applications &#8594; Add/Remove. In the top right, change the setting to All available applications. Select Other in the left panel and then select the Ubuntu restricted extras package. Click Apply Changes.

And then do this:
* Open your terminal (Applications > Accessories > Terminal) then copy and paste the following commands into the terminal window. Enter your user password when prompted.
sudo wget http://www.medibuntu.org/sources.list.d/`lsb_release -cs`.list --output-document=/etc/apt/sources.list.d/medibuntu.list
sudo apt-get -q update; sudo apt-get --yes -q --allow-unauthenticated install medibuntu-keyring; sudo apt-get -q update

And then do this:
64 Bit Ubuntu Users:
sudo apt-get install libdvdcss2 w64codecs


That would be an interesting use of virtualization. You might want to research VirtualBox. There is one version in Add/Remove Software, but you will want to download the version from Sun Microsystems, as it has USB support.

---

### Post by Eldera on 2009-07-29
Thank you, ajgreeny & TA. I will follow your instructions later this evening now I am sure what to do.

[quote=ajgreeny]It it ain't broke, don't fix it. The trouble is, if you always kept to that rule, you would never try anything new, and I like to test things out.[/quote]

I love to try new things, too, unfortunately it usually takes about ten tries to get something right. 

Ah, well
[quote=a very old Hobbit movie]The greatest adventure is what lies ahead.[/quote]

Edit: Project completed successfully, Thank you again.

---

### Post by macabrem on 2009-09-20
I read this page about restricted formats and was a little confused:
[http://knowledge76.com/index.php/Installing_Restricted_Formats](http://knowledge76.com/index.php/Installing_Restricted_Formats)

When I get my Starling Netbook, I want to make sure I can play mpg, avi, mpeg, youtube, and about any video file.

Is this actually a three part process?  The above link appears that I have to:
1) Install "Ubuntu Restricted Extras" by doing this "Click Applications &#8594; Add/Remove. In the top right, change the setting to All available applications. Select Other in the left panel and then select the Ubuntu restricted extras package. Click Apply Changes."

Then...

2) Open a terminal to install a separate package from Medibuntu by doing this "Open your terminal (Applications > Accessories > Terminal) then copy and paste the following commands into the terminal window. Enter your user password when prompted.
sudo wget http://www.medibuntu.org/sources.list.d/`lsb_release -cs`.list  --output-document=/etc/apt/sources.list.d/medibuntu.list
sudo apt-get -q update; sudo apt-get --yes -q --allow-unauthenticated install medibuntu-keyring; sudo apt-get -q update"

3) Then do this since I will be using 32 bit Ubuntu: "sudo apt-get install libdvdcss2 w32codecs" ?  

Is that pretty accurate?  Or, does #1 and #2 do the same thing except #1 is GUI and #2 is command line?

Also, I noticed that the directions on the Medibuntu page are slightly different than the above: [https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)

So basically, I am wanting to know what is accurate, and what the minimum I need to do to get most video formats working along with their audio, with a Starling Netbook fresh from S76?  I am comfortable using a terminal although I'm still trying to learn what a lot of the commands actually do.  So, I don't want to "double do" myself by typing commands in the terminal if I already installed everything I need via adding programs in the GUI.

Thanks for your help.

---

### Post by Zimmer on 2009-09-20
Try reading this instead
[https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)

---

### Post by macabrem on 2009-09-20
I've actually read that link too, which opened the door to more questions.  Should I just click that link to install the extras? 

Also, can one just install Mplayer and VLC and be able to play the restricted formats?

---

### Post by HotShotDJ on 2009-09-20
> **macabrem said:**
> I've actually read that link too, which opened the door to more questions.  Should I just click that link to install the extras? 

Also, can one just install Mplayer and VLC and be able to play the restricted formats?Macabrem:  Please follow the instructions given by System76 at [http://knowledge76.com/index.php/Installing_Restricted_Formats](http://knowledge76.com/index.php/Installing_Restricted_Formats)   -- while you can probably accomplish some of the same things using different methods, the instructions on the System76 have two distinct advantages... 1) they are correct, and 2) they are tested and supported by System76.

Once you have done that, you'll be able to install almost any media player (such as Mplayer or VLC) and enjoy playing things encoded with restricted formats.

---

### Post by Eldera on 2009-09-20
I wondered about the tutorial, too. And got the answer in post 3, this thread.

I have only used Rythumbox for Cd and Totem for DVD. I haven't had time to study video apps. The tutorial worked for the things I needed. 

Hot Shots advice sounds very good. I would follow it.

---

### Post by macabrem on 2009-09-20
Eldera - I guess great minds think alike. :)  Thanks for the link to the previous thread.  

Hotshot - sounds like solid advice.  Thanks to everyone responding.  :)

---

### Post by Zimmer on 2009-09-21
Thank You! 
By replying and then seeing the link to Medibuntu (which I had lost in a recent upgrade) I have discovered why a recent USB install was making the CD drive sound like a sick Chinook  when I popped a DVD movie in!  I had forgotten the libdvdcss2 .

---

### Post by Elfy on 2009-09-21
Threads merged

---

