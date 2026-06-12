---
title: "Xubuntu and nm-applet after today's update"
date: 2012-02-21
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by prana on 2012-02-21
This is with Xubuntu i386.

WIth todays update to network-manager, my nm-applet behaves strangely before crashing. I see two icons connecting to the network. One is a panel item and the other is part of the indicator plugin. They both change to a rotating circle and after a while, both crashed. Here is a bug for the crash.


[https://bugs.launchpad.net/ubuntu/+source/network-manager-applet/+bug/928594](https://bugs.launchpad.net/ubuntu/+source/network-manager-applet/+bug/928594)

Should I create a separate bug for the duplicate indicator on the panel?

---

### Post by prana on 2012-02-21
Anyone else running Xubuntu have this duplicate nm-applet problem? Or a workaround for solving it?

Thanks.

---

### Post by prana on 2012-02-21
As far as I can tell, there is a new entry in the file 

~/.config/xfce4/xfconf/xfce-perchannel-xml/xfce4-panel.xml


   <property name="plugin-4" type="string" value="systray">
      <property name="show-frame" type="bool" value="false"/>
      <property name="size-max" type="uint" value="22"/>
      <property name="names-visible" type="array">
        <value type="string" value="xfce4-power-manager"/>
        **<value type="string" value="networkmanager applet"/>**
        <value type="string" value="swt"/>
        <value type="string" value="dropbox"/>
      </property>
    </property>


I tried deleting that line as a wordaround to get rid of the duplicate nm-applet entry in the panel but the next time I log in, the file gets overwritten and I don't get a chance to find out if the change worked. Is there any way to stop that from happening?

---

### Post by ranch hand on 2012-02-22
I do not have that problem.   I am running 64 bit but other wise pretty standard install.  I upgrade by chroot earlier from my Debian install and just popped over to check the bugger.

Have done another update/upgrade cycle to see that everything worked in native terminal.  Got a new upgrade for nm. you may want to check that.  Could be that it is the one that screwed you if your repo was ahead of mine too.

Am going to reboot and will report back.

---

### Post by ranch hand on 2012-02-22
Yup, I now have 2.  They both appear to be nm.  Kind of wondered if wicd got snuck in and appeared too.  That is not the case.

If you are the guy that filed the bug the report is that you are using the 64bit version as am I.

Added my me too and mentioned the 2 instances of the applet.  Thing holds up for a while and then just seems to give up.

Better post this before it quits again.

---

### Post by ranch hand on 2012-02-22
Just to add to that last post.

After posting I disabled networking and then re-enabled it.  Came up fine with both applets.

While I am happy to be back on Debian and prefer the cleaner Xfce4.8 that they use, this 12.04 version of Xubuntu is really looking very nice.  I think it is going to be are great release.

---

### Post by ventrical on 2012-02-22
Had the same problem with Ubuntu yesterday. nm-applet crashing.  It all worked out after update.

---

### Post by Elfy on 2012-02-22
Got two icons here as well - no problems with networking though.

---

### Post by prana on 2012-02-22
Yup, nm is no longer crashing but I have two icons - one in the systray and the other as part of the indicator plugin.

I suppose it is better to wait for the two icon problem to get resolved. I think it is being caused by a new version of nm-applet where they redid some of the code. I would venture to guess that xfce4-indicator-plugin hasn't caught up yet. Here is the latest nm-applet changelog:

**network-manager-applet (0.9.2.0+git.20120126t000800.5151959-0ubuntu3) precise; urgency=low**

  * debian/patches/lp829673_gconf_hide_applet.patch: allow toggling the applet
    visibility. (LP: #829673)
  * debian/patches/nm-applet-use-indicator.patch: completely replace the old
    wireless menu item creation code overriding NMNetworkMenuItem objects to
    rewrite it more simply with GtkImageMenuItems. This should really take care
    of the memory leaks. (LP: #930491)
 -- Mathieu Trudel-Lapierre <mathieu-tl@ubuntu.com>   Mon, 20 Feb 2012 13:58:49 -0500

---

### Post by C S on 2012-02-22
Yes, I have two applets showing up my xfce panel.  One shows up as part of xfce4-indicator-plugin; the other shows up in the notification area.  Interestingly, I see only one in Unity.  My networking is fine however.  I am running the 64-bit version of 12.04, but as other posts indicate, it seems to be some kind of bug/conflict between the xfce4-indicator-plugin and nm-applet.

---

### Post by Elfy on 2012-02-23
> **prana said:**
> 
Should I create a separate bug for the duplicate indicator on the panel?Unless Sam_ is you there is one


[https://bugs.launchpad.net/ubuntu/+source/network-manager-applet/+bug/938380](https://bugs.launchpad.net/ubuntu/+source/network-manager-applet/+bug/938380)

---

### Post by prana on 2012-02-23
> **forestpiskie said:**
> Unless Sam_ is you there is one


[https://bugs.launchpad.net/ubuntu/+source/network-manager-applet/+bug/938380](https://bugs.launchpad.net/ubuntu/+source/network-manager-applet/+bug/938380)

No, I am not Sam so I added a "me too".

Thanks.

---

### Post by Elfy on 2012-02-23
Thanks :)

---

### Post by ranch hand on 2012-02-23
Added my me too to that bug too.

Interested to see that someone said they had it on Unity too.

---

### Post by Elfy on 2012-02-24
None at all now.

---

### Post by longxin on 2012-02-25
yesterday the nm-applet indicator was missing in the panel after a update?but the network could be auto connected...does any has the same problem?:confused:

---

### Post by Elfy on 2012-02-25
I did and do still - as I said 19 hours ago :)

---

### Post by prana on 2012-02-25
Yes, nm-applet is missing on my desktop as well.

---

### Post by bobcollard on 2012-02-25
> **longxin said:**
> yesterday the nm-applet indicator was missing in the panel after a update?but the network could be auto connected...does any has the same problem?:confused:
Yes, same thing here.  No icon and no access to a GUI to see if it's working, BUT, if it isn't then this won't go through.  LOL

---

### Post by ranch hand on 2012-02-25
Have any of you added comments to the bug?

I have had a couple real busy days and have not even been over there to see what conditions are since my last post.

---

### Post by Elfy on 2012-02-26
> **ranch hand said:**
> Have any of you added comments to the bug?

I have had a couple real busy days and have not even been over there to see what conditions are since my last post.

I did - things are afoot I believe. Fix committed.

---

### Post by ranch hand on 2012-02-26
I seem to have the same condition.  No applet at all.

We were asked to comment at the bug or to file a new one.  As I think this is the result of the fix I just added a comment.

Probably be good for others to do that to.
[https://bugs.launchpad.net/ubuntu/+source/network-manager-applet/+bug/938380](https://bugs.launchpad.net/ubuntu/+source/network-manager-applet/+bug/938380)

I did ask if filing  new bug would be better but it really sounded like a pretty straight forward thing to fix so why make more reports to wade through?

---

### Post by Elfy on 2012-02-26
I had - I'd said almost the same as you :)

---

### Post by ranch hand on 2012-02-26
Well I guess that is all we can do.

I bet it gets straightened out pretty soon.

---

### Post by Elfy on 2012-02-28
One applet showing now.

Though you need to fiddle in gconf-editor (or cli) to get it to show.

Perhaps it does need a seperate Xubuntu bug - waiting for confirmation on the bug report.

Edit - apparently not.

---

### Post by jefsview on 2012-02-29
the updates came a day or so ago. It's all fixed, and the aplet shows up in the notification area.

12.04 has been very stable, and is so much faster than 11.10. Thunar always dragged in 11.10, but zips along now. Very pleased with this release so far.

The nm-applet disappearing was about the one recent headache. But can live with that.

-- jeff

---

