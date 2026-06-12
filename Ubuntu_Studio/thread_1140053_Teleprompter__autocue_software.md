---
title: "Teleprompter / autocue software"
date: 2009-04-27
forum: Ubuntu Studio
---

### Post by ginestre on 2009-04-27
I've been looking for a Linux solution for teleprompter software for a fair while, as have others, but without success. So now I've been pointed at a solution I'd like to pass it on. Thanks to Jon for showing me this. 

It's a Russian built Python script called PyBookReader. Info at 
[http://wiki.linuxquestions.org/wiki/PyBookReader](http://wiki.linuxquestions.org/wiki/PyBookReader)

Here are the hand-holding instructions Jon gave me to get it up and running:

download the file. 
tar -xzvf FILE
cd into the directory
sudo apt-get install libxml2-dev python-gtk2-dev
sudo python setup.py install
pybr

Hope that helps someone else.

---

### Post by mjpatey on 2009-05-08
Love it!  Font size and foreground/background colors can be adjusted to look just like a prompter.

One trick I discovered... if 100% speed isn't fast enough, make the font a tad smaller and more words will go by in the same amount of time.  :-)  Also, I just did a test using a script from a recent project, and if I'm prompting for myself (as in a one-person operation like a podcast), it's easy to use the mouse's scroll wheel to occasionally kick the script forward and back when needed.  May not work as well if you're prompting someone else, since the jump ahead or back is pretty abrupt when using the scroll wheel.

One thing I can't find is a "Home" feature to return to the beginning, but I imagine that could be done with the bookmarks feature.

ginestre, this is a great find!  Thanks for posting about it.

---

### Post by mjpatey on 2009-05-08
A small caveat:  maybe stay away from using the cursor up/down keys to fast-forward/rewind... if I hold them down for too long, the "Pause" key no longer works, and the script just keeps scrolling.

The mouse wheel works just fine for that purpose, though.

---

### Post by mart_k on 2009-05-14
I wrote autocue software for myself. It wasn't really designed to distribute or publish it, but if you wish I have no problem with putting it somewhere (under GPL licence).

My program uses the foot pedals from my racing wheel to set the speed of the scrolling text. Basically, every joystick will do. You can prepare 12 pages for text (there is no limit in the length of the page), and switch between pages with F-buttons.

Because it was designed to be used only by myself, many things are hard-coded, and the interface isn't very good. But I can point you in the right directorion how to change the hard-coded settings. Qt4 and plib are required to compile it.

Regards,

Mart

---

### Post by mjpatey on 2009-05-14
Mart,

Thanks, I'd love to give it a try.  If you post the download location to this thread, it would be a nice contribution to the community!  The e-book reader mentioned above works very nicely, as well, but one of the beauties of free software is choice!

Thanks for posting, and I look forward to trying your software if you do make it available.  I'll have to dig up an old joystick, I suppose... will it work with keyboard or mouse controls, as well?

---

### Post by mart_k on 2009-05-14
You can find it at [http://home.kpn.nl/k.b5/mart/autocue0.0.1.tar.gz](http://home.kpn.nl/k.b5/mart/autocue0.0.1.tar.gz) . There is some documentation in quick_doc.txt. My email address also is in some of the source files.

It doesn't have support for keyboard or mouse. It proberbly isn't that hard too add, but it was not neccesairy for me. If keyboard control would be sufficient, I would proberbly used the autoscroll function of Konqueror. This way, I have my hands free. I also use a large font which means that the speed must be changed often.

---

### Post by ghostcatzero on 2011-06-07
Mart,

Is there a way you or someone else could make your autocue app controlable via keyboard or Bluetooth clicker? I want to produce some videos and can't find a useable teleprompter app anywhere. I don't have any gaming paraphernalia like joysticks or pedals, and I would like to be standing and walking around while I'm talking in the videos, not just sitting at my computer while recording.

---

### Post by mart_k on 2011-06-08
How do you expect a keyboard autocue to work? I think there are two options:[LIST=1]
[*]Use the keys such that the text goes down a bit
[*]Use the keys such that the text moves slower or faster.
[/LIST]

I think both are possible with browser software. You can make a very simple html-page containing your text in a text-size and font you can easily read. The you use the following method to use the autocue:[LIST=1][*]Open your file in a web-browser and use the keys if you need to scroll[*]Open your file in Konqueror and use the up- or downarrow in combination with the SHIFT-button to go slower or faster.[/LIST]

Maybe you have a different way in mind of controlling the autocue with keys. The main drawback of the first way is that the text moves suddenly when pressing a key. It can be hard to continue reading because you need to refocus on the text. This is a problem for me because for me reading text is time-critical (if I read slower through some circumstances, I read too slow to say the text).

I don't know what kind of device your bluethooth clicker is. If it is recognized as usb HID (human interface device), you might be able to get those keys interpreted as arrow keys.

---

### Post by tg3793 on 2011-09-16
Perhaps you guys would be interested in this solution. It's called [Manual Works Prompter]("http://download.freewarefiles.com/files/ManualWorksPrompterV54.zip") 5.4 and it's only a 20.6KB HTML file that I found.

The author designed it for Windows and IE but he also gives the 'go' to edit it for one's liking. 

It looks quite good from what I've been able to see but I don't know enough about Java Script to get it to load the text file as it is designed to do.

I hope my digging [and finding a good starting point] benefits others including myself.

---

