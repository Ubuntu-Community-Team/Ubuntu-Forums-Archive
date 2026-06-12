---
title: "Install Rhapsody on Ubuntu Linux"
date: 2007-07-10
forum: The Cafe
---

### Post by sookoon on 2007-07-10
Because the solution was nestled deep on the fifth page of someone's post, I felt it necessary to post Ciscosurfer's solution on its own post, because IT WORKS!!!  Thanks Ciscosurfer!

---------------------------------------------------------------------------------------------

OK Ladies and Germs, here's the dirt on how to get the Rhapsody online service/player to work for you (and quick hack--ymmv, but it worked for me). This assumes that a) you have a current build of FF or SF (read: FF 2.0 or SF 2.0) installed on your system, and b) you're willing to mess around a little to get it to work:

If you previously installed the Rhapsody plugin in versions above FF 1.0.1 and before FF 2.0 (or Swiftfox 2.0), then the plugin will be ready for you to use online at Rhapsody.com.

If you have recently installed Ubuntu (read: fresh install; Edgy or the like), and no older versions of FF exist on your system, then you have go through a few hoops to get the Rhapsody plugin to work.

Step 1: Download FF 1.5

Step 2: Run FF 1.5 (DO NOT INSTALL), go to Rhapsody.com, search for your favorite artist, click the link to play a song.

Step 3 (hack, part 1): A popup will load asking if you'd like to download the Rhapsody plugin. Click yes. The download will proceed. Once complete, close out your browser.

Step 4 (hack, part 2): At this point, your new Rhapsody plugin will be installed in your main firefox directory located at ~/.mozilla/plugins and ready to use.

Step 5 (hack, part 3): Running from your current FF or SF build. To get sound to work, you need to issue the old 'aoss' hack, either from the console or from a launcher. For example, if you want to run FF from the command line, you would issue
Code:

aoss firefox

For SF, you would issue
Code:

aoss /opt/swiftfox/swiftfox

You can add either one of these to your currect launchers or create new ones to suit your needs.

I came up with this because my current build of FF and SF wouldn't allow me to download the plugin from Rhapsody in order to use the online player (and perhaps later, use it for subscription to their service?)

If you can get sound to work without the alsa oss hack, more power to you! I couldn't, so I needed to prepend my command.

Enjoy!

---

