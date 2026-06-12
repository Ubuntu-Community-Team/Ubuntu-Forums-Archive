---
title: "GIMP 2.7.1 is out!"
date: 2010-07-01
forum: The Cafe
---

### Post by altonbr on 2010-07-01
Release notes: [http://www.mail-archive.com/gimp-developer%40lists.xcf.berkeley.edu/msg20312.html]("http://www.mail-archive.com/gimp-developer%40lists.xcf.berkeley.edu/msg20312.html")

PPA: [https://edge.launchpad.net/~matthaeus123/+archive/mrw-gimp-svn]("https://edge.launchpad.net/%7Ematthaeus123/+archive/mrw-gimp-svn/+packages")

or

```
sudo add-apt-repository ppa:matthaeus123/mrw-gimp-svn; sudo aptitude update; sudo aptitude upgrade; sudo aptitude install gimp
```

---

### Post by alexan on 2010-07-01
> UI Changes and Improvements

There have been some significant changes to the UI. The docking bars have been removed and replaced with overlayed highlights. The dockble drag handle has been removed and the dockable menu button has been moved up to the tabs. A new Automatic tab style has been added which makes dockable tabs use the available space. It has been made possible to have many columns of docks in a single dock window. To make dock window titles managable, only show the active dockable in the dock window title. A single-window mode has been added (still in the works, in particular, it is not possible to start up in single-window mode yet). 

Support for layer groups have been added. They allow you to organize your image into small parts. Still some things missing, like allowing to apply layer masks to groups, and a PDB API. 

Text editing with the Text Tool is now performed on-canvas instead of in a separate window. The editing on-canvas is rather sophisticated and tries to mimic text editing capabilities of GtkTextView. There are still some polishing left to do here, but it works rather nice already. This feature was developed during Google Summer of Code 2008. 

An infrastructure has been added that allows to embed user interface elements on the canvas. This is currently used for text styles in the text tool, and (experimentally) when a color correction tool is invoked while the canvas is in full-screen mode. 

It is now possible to tag GIMP resources such as brushes and patterns. The tagging is performed from the respective dockables e.g. the Brushes dockable, and it is possible to filter resources based on these tags. The tags are saved to an XML file, external to the data files themselves. This feature finally enables grouping of resources and the plan is to add a bigger set of default resources for GIMP 2.8. It is possible to tag multiple resources simultaneously in the UI. There are still work that needs to be done here, for example providing a set of default brushes. This feature was developed during Google Summer of Code 2008. 

A rather big conceptual change is that saving and exporting images are clearly separated activities. Saving an image can only be done in the XCF format, to export into other formats 'File->Export...' needs to be used. There are some optimizations for alternative workflows such as opening a jpg, polishing it, and quickly exporting back to the original file. This conceptual change has also allowed us to get rid of the annoying dialogs that warned about the flatting of images when saving to non-layered formats. The complete UI spec for this can be found here. 

Since the keyboard shortcuts Ctrl+E and Ctrl+Shift+E has been taken over by the image export mechanisms, new keyboard shortcuts have been setup for "Shrink Wrap" and "Fit in Window", namely Ctrl+R and Ctrl+Shift+R respectively. 

Enhancements have also been made to the size entry widget, the widgets that are used for most of the x, y, width, height input. For example, in the scale dialog it is now possible to write "50%" in the Width field to scale the image to 50% of the width. Expressions such as "30in + 40px" and "4 * 5.4in" works too. 

The layer modes have been rearranged into more logical and useful groups based on the effect they have on compositing of a layer. Layer modes that makes the composite lighter are in one group, layer modes that makes the composite darker in another group, and so on. 

It has been made possible to Alt+Click on a layer to create a selection from it. Add, subtract and intersect modifiers Ctrl, Shift and Ctrl+Shift keys works too. This makes it easy to compose contents of a layer based on the contents of other layers, without detours. 

GIMP now supports rotating brushes and has had additional enhancements to the brush dynamics engine, for example allowing to base dynamics on tilt and dynamically change the aspect ratio of brushes. The Google Summer of Code 2009 Advanced GUI for Brush Dynamics code has also been merged, enabling such things as brush dynamics presets. 

A question that often arises is how to change the UI language in GIMP, which has traditionally been a bit cumbersome. Not any longer, it is now possible to change language in Preferences.
[http://www.gimp.org/release-notes/gimp-2.7.html](http://www.gimp.org/release-notes/gimp-2.7.html)

---

### Post by alexan on 2010-07-01
Great, I can no longer control the pen pressure behaviors. :\


Edit: Ok, I get it: they moved the pen dynamics in a separate tags

---

### Post by Lucradia on 2010-07-01
[http://www.gimp.org/](http://www.gimp.org/)

If it doesn't say on the website's frontpage, then it isn't true.

Also have to wait like a month or two before GIMP Win comes out too, if it was final that is.

Also, next time, don't make it look like it's a final release from your thread title.

---

### Post by LMP900 on 2010-07-01
> **Lucradia said:**
> [http://www.gimp.org/](http://www.gimp.org/)

If it doesn't say on the website's frontpage, then it isn't true.

Also have to wait like a month or two before GIMP Win comes out too, if it was final that is.

Also, next time, don't make it look like it's a final release from your thread title.

Yeah, I definitely thought that it was some sort of final release. I forget they do odd-even numbering for development-final versions.

---

### Post by wykedengel on 2010-07-01
Thanks for the share. I think I will wait for the final release to hit before I download it.

---

### Post by Legendary_Bibo on 2010-07-01
I like the features, but I hear 2.7 is horribly unstable. I actually can't wait for 2.8. I love that we finally get a single window with everything docked. Also we get rotating brushes woohoo! I honestly would have to open up a new transparent canvas paint on it, rotate the image, save to clipboard then use it as a brush. It was too annoying.

---

### Post by aklo on 2010-07-01
Still waiting for official release.

GIMP needs folder in the layer panel like what photoshop has. I did a web design with like 50 layers and finding a particular layer is one time consuming task.

---

### Post by JDShu on 2010-07-01
I can't wait until GEGL gets fully integrated. That probably won't happen until 2011/2012 though when 2.10 comes out.

---

### Post by NightwishFan on 2010-07-01
Glad it is finally moving forward. Gimp is one of my favorite programs. :) Anyone know if this will be in Maverick? I will have to look in the Debian repos. If they build it there it will land in Ubuntu sometime.

---

### Post by JDShu on 2010-07-01
> **NightwishFan said:**
> Glad it is finally moving forward. Gimp is one of my favorite programs. :) Anyone know if this will be in Maverick? I will have to look in the Debian repos. If they build it there it will land in Ubuntu sometime.

GIMP has been cut from default installs of Ubuntu. As for whether its in the repos, 2.7 is unstable and the stable, 2.8 isn't expected to be out until December. So no, it won't be in the default Maverick repositories.

---

### Post by NightwishFan on 2010-07-01
I am not sure I understand but I know you are trying to be helpful. I doubt they would remove Gimp from main even though it is not installed by default.

---

### Post by JDShu on 2010-07-01
Ah, what I mean is that the Gimp in the Maverick Repositories will be version 2.6, same as the current one.

---

### Post by NightwishFan on 2010-07-01
Thanks my friend. Well I prefer to be conservative anyway. Forgive my confusion.

---

### Post by nilarimogard on 2010-07-02
The GIMP package from the mrw-gimp-svn PPA dates back to February and is as buggy as hell!

---

### Post by philinux on 2010-07-02
Current Maverick version is.

Gimp Version table:
     2.6.8-2ubuntu1.1 0

---

### Post by Half-Left on 2010-07-02
AWESOME! Rotating brushes, damn I need that.

---

### Post by Half-Left on 2010-07-02
> **aklo said:**
> Still waiting for official release.

GIMP needs folder in the layer panel like what photoshop has. I did a web design with like 50 layers and finding a particular layer is one time consuming task.

Yeah, layer grouping would be nice.

---

### Post by forrestcupp on 2010-07-02
The unstable development version of Gimp 2.7.1 has been out for a very, very long time.  This thread is extremely old news.

---

### Post by Half-Left on 2010-07-02
> **forrestcupp said:**
> The unstable development version of Gimp 2.7.1 has been out for a very, very long time.  This thread is extremely old news.

Eh? 2.7.1 > Wed, 30 Jun 2010

---

### Post by Lucradia on 2010-07-02
> **Half-Left said:**
> Eh? 2.7.1

I used GIMP 2.7.1 a few months back actually, so yes, old news.

---

### Post by Half-Left on 2010-07-02
> **Lucradia said:**
> I used GIMP 2.7.1 a few months back actually, so yes, old news.

Well it's only been released 3 days ago officially. Why does using SVN make it old news?

---

### Post by forrestcupp on 2010-07-02
> **Half-Left said:**
> Well it's only been released 3 days ago officially. Why does using SVN make it old news?

I don't know what that's all about.  It's still an unstable development version.  It's not in any different state than it was a few months ago when I tried it out.  I even found a Windows binary installer for it a few months ago.

I don't see any difference in anything, so I don't know why they decided to just slap that date on it.

Edit:
I take everything I said back.  I just checked, and the version I installed in March was 2.7.0.  Sorry.  That's cool that they're making progress.

---

### Post by Half-Left on 2010-07-02
You like me will be happy to know that 2.7.1 does have layer grouping. :)

[IMG]http://img375.imageshack.us/img375/9066/gimplayergroup.png[/IMG]

---

### Post by Half-Left on 2010-07-02
I actually  made a video of the new features in 2.7.x because it's worth it. Exciting new features. :) 

[http://www.youtube.com/watch?v=ewtq3IHHASg](http://www.youtube.com/watch?v=ewtq3IHHASg)

I should really talk over a mic but I just don't get enough quiet time to do it.

---

### Post by Legendary_Bibo on 2010-07-02
> **Half-Left said:**
> You like me will be happy to know that 2.7.1 does have layer grouping. :)

[IMG]http://img375.imageshack.us/img375/9066/gimplayergroup.png[/IMG]
Oh wow, not a feature I was looking for, but it still looks awesome. Did they by chance have a fix for using 'fill' on objects painted with the paintbrush? When I paint object with the paint brush I like the softening effect they have but when I fill them there's that white line surrounding the filled area. Here's an example of what I'm talking about. Is there a technique you guys use to fix this problem, because all I do is zoom in and fill in the space.

---

### Post by madjr on 2010-07-02
> **NightwishFan said:**
> Anyone know if this will be in Maverick? I will have to look in the Debian repos. If they build it there it will land in Ubuntu sometime.


ubuntu is planning a **post-release** repo for new apps

[http://www.webupd8.org/2010/06/new-post-release-repository-for-new.html](http://www.webupd8.org/2010/06/new-post-release-repository-for-new.html)

so yea you will see a bunch of new apps for maverick 

yay !
:P

---

### Post by Mr. Picklesworth on 2010-07-02
> **Legendary_Bibo said:**
> Oh wow, not a feature I was looking for, but it still looks awesome. Did they by chance have a fix for using 'fill' on objects painted with the paintbrush? When I paint object with the paint brush I like the softening effect they have but when I fill them there's that white line surrounding the filled area. Here's an example of what I'm talking about. Is there a technique you guys use to fix this problem, because all I do is zoom in and fill in the space.

Take a look at the Tool Options panel when you're using Bucket Fill, and play with the Threshold property.


> **NightwishFan said:**
> I am not sure I understand but I know you are trying to be helpful. I doubt they would remove Gimp from main even though it is not installed by default.
Quite correct. GIMP is in main and very well supported. It just isn't on the disk for the default install of Ubuntu. (It is for Ubuntu Studio!)

GIMP 2.7 is an unstable branch, though, so it won't be landing in Maverick for that reason. (Unless 2.8 releases really soon; I don't know the schedule, to be honest). With many free software projects, stable releases are given even numbers for their versions while unstable ones are given odd numbers.

I'm hoping 2.8 will see a lot more work for single-window mode, though. There was a really amazing mockup where the tabs for open files could be dragged to pull out little previews, and where the list of open images also had closed (recent) files seamlessly blended in. It was magical stuff :)

---

### Post by Half-Left on 2010-07-02
Sorry, I think I've lost the plot. Yes Threshold.

---

### Post by Half-Left on 2010-07-02
> **Mr. Picklesworth said:**
> 
I'm hoping 2.8 will see a lot more work for single-window mode, though. There was a really amazing mockup where the tabs for open files could be dragged to pull out little previews, and where the list of open images also had closed (recent) files seamlessly blended in. It was magical stuff :)

See my video I posted above. 2.7.1 has such features. :)

---

### Post by NightwishFan on 2010-07-02
> **madjr said:**
> ubuntu is planning a **post-release** repo for new apps

[http://www.webupd8.org/2010/06/new-post-release-repository-for-new.html](http://www.webupd8.org/2010/06/new-post-release-repository-for-new.html)

so yea you will see a bunch of new apps for maverick 

yay !
:P

Thanks Mr. Pickles. I misunderstood the poster vastly, but he cleared it up.

Yeah I read about that, I am looking forward to that a lot. Some of my close friends who use Ubuntu will be impressed with that.

---

### Post by JDShu on 2010-07-02
> **Mr. Picklesworth said:**
> 
I'm hoping 2.8 will see a lot more work for single-window mode, though. There was a really amazing mockup where the tabs for open files could be dragged to pull out little previews, and where the list of open images also had closed (recent) files seamlessly blended in. It was magical stuff :)

Single window mode is the big thing for 2.8 I think you will be glad! Its just that full GEGL integration is being pushed back to 2.10 which disappoints me a little.

---

