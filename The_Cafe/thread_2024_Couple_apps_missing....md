---
title: "Couple apps missing..."
date: 2004-10-25
forum: The Cafe
---

### Post by dawynn on 2004-10-25
I moved over from Debian Linux (Testing) to Ubuntu (Warty) this last week.  After spending some time downgrading most of my system, pretty much everything is at the Ubuntu level.  With Apt references to the 'main restricted universe multiverse' sections of Ubuntu, there are just a few programs that I haven't been able to find any versions of.

I'm wondering if there's any chance we could get these added either to the Universe (or Multiverse) repository in Warty -- or at least make sure they're slated for inclusion in Hoary:

**Gnomesword** -- (gnomesword.sourceforge.net)  This is a Bible study tool.  Strangely, Warty Universe has several support packages from the Sword project, but only the KDE main tool (Bibletime), even though Ubuntu prefers Gnome over KDE.

Note: I noticed that Gnomesword had been taken out of Debian Testing.   I tried installing it from Debian Unstable on my Ubuntu machine.  I received a Seg Fault from both Bibletime and Gnomesword using the Ubuntu libraries.  I had to update the libsword4 library in order to correct this fault.  Conclusion: the libsword4 library in Ubuntu Universe is broken.

**Lilypond** -- (lilypond.org)  This is a music typesetting tool.  It's part of the GNU project.  Again, strangely, Warty Universe includes the tool Denemo, which is "A Gtk+ frontend to GNU Lilypond", then forgets to include packages for Lilypond or Lilypond-doc.

The previous two apps were included in Debian Testing, but not available in Ubuntu Warty.  This next one is in neither, but would be nice to consider for Hoary...

**xu4** -- (xu4.sourceforge.net)  Ultima 4 for multiple platforms.  Think Exult (which is in Warty Universe) for Ultima 4.

Those were the only missing apps that I truly cared about.  It would be nice to have some kind of website to recommend such things either for current or future releases.

Great job on the first release!

---

