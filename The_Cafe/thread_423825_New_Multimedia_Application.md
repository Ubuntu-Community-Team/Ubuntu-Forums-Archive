---
title: "New Multimedia Application"
date: 2007-04-26
forum: The Cafe
---

### Post by gozza11 on 2007-04-26
Hello everyone.

I have created a new multimedia application using Gtk# and the Mono runtime.
It is called Dissent, available at [www.dissent-project.org](www.dissent-project.org)

It still has a lot of kinks to work out but it is still a very young project.

So far it has the following features:
  -  Gstreamer media engine which allows mp3, ogg, avi, mov files to play.
  -  Current playing song notification  (like on Banshee)
  -  RSS and Podcast support
  -  Internet radio support
  -  Simplistic theatre
  -  Built in browser  (using Gecko#)

Essentially its a program I created to help keep me busy and I hope it is received well by the community.
Note that I do not intend to replace great programs like Totem or Rhythm Box. I just wanted to combine some of the more frequent programs into one simplistic program on steroids.

Any comments welcomed :)

Thank You
Goran

(ps. full feature list and screenshots are on the site)

---

### Post by Tomosaur on 2007-04-26
It refuses to run, but it looks great. I'm getting this error:
```

System.TypeInitializationException: An exception was thrown by the type initializer for Gecko.WebControl ---> System.DllNotFoundException: /usr/lib/firefox/libgtkembedmoz.so
  at (wrapper managed-to-native) Gecko.WebControl:gtk_moz_embed_get_type ()
  at Gecko.WebControl.get_GType () [0x00000] 
  at GtkSharp.GeckoSharp.ObjectManager.Initialize () [0x00000] 
  at Gecko.WebControl..cctor () [0x00000] --- End of inner exception stack trace ---

  at <0x00000> <unknown method>
  at DissentGtk.NewsWindow..ctor (Glade.XML gxml) [0x00000] 
  at DissentGtk.Dissent..ctor (System.String[] args) [0x00000] 
  at DissentGtk.Dissent.Main (System.String[] args) [0x00000] 

```

---

### Post by gozza11 on 2007-04-26
Yea, I have been hearing that a lot lately. I should really add something on the website like a howto or something.

Essentially its missing the Gecko library which is usually installed by firefox.
All you need to do is add a line in the ld.so.conf file pointing to the directory that has the  libgtkembedmoz.so file.  something like  '/usr/lib/firefox'
dont forget to run ldconfig afterwards.

you could also just export the LD_LIBRARY_PATH environment variable if your executing through the terminal.

For the life of me I cannot find a way to make this work on all linux flavours since libgtkembedmoz.so is all over the place. Maybe i should check if it exists at runtime then disable the specific features if it doesnt exist.. (if it is at all possible)

is this with the ubuntu binary file?
perhaps you will have more luck compiling from source.. the deb file worked in my debian and ubuntu edgy eft setup...

---

### Post by Tomosaur on 2007-04-26
Thanks for the info. The download I used was actually the Dissent 0.1 for Debian (Sid). I didn't download the Ubuntu specific one because I don't have a 64 bit machine. I'll try compiling from source, if that doesn't I'll try your fix.


EDIT:
Nope, compilation returned an Error, something about my Mono runtime being broke? I also tried your fix, but it didn't work.

---

### Post by gozza11 on 2007-04-26
what error did you get during compilation?
is it a missing reference or actual code error?

---

### Post by BLTicklemonster on 2007-04-29
> **gozza11 said:**
> Yea, I have been hearing that a lot lately. I should really add something on the website like a howto or something.

Essentially its missing the Gecko library which is usually installed by firefox.
All you need to do is add a line in the ld.so.conf file pointing to the directory that has the  libgtkembedmoz.so file.  something like  '/usr/lib/firefox'
dont forget to run ldconfig afterwards.

you could also just export the LD_LIBRARY_PATH environment variable if your executing through the terminal.

For the life of me I cannot find a way to make this work on all linux flavours since libgtkembedmoz.so is all over the place. Maybe i should check if it exists at runtime then disable the specific features if it doesnt exist.. (if it is at all possible)

is this with the ubuntu binary file?
perhaps you will have more luck compiling from source.. the deb file worked in my debian and ubuntu edgy eft setup...

Do what? I got the same error, but you lost me there.

---

### Post by gozza11 on 2007-04-29
here is a link to someone who had the same problem with fedora 6
  [http://sourceforge.net/tracker/index.php?func=detail&aid=1671355&group_id=186001&atid=915529]("http://sourceforge.net/tracker/index.php?func=detail&aid=1671355&group_id=186001&atid=915529")


you have to make sure that the program can find the file  libgtkembedmoz.so.

im not entirely sure but for ubuntu the file might be in  '/usr/lib/xulrunner'
you can find out exactly by typing in the following in the command line

        find /usr/lib -name libgtkembedmoz.so

and then try the following two commands to see if its working

        export LD_LIBRARY_PATH=/usr/lib/xulrunner
        dissent

if the file isnt in /usr/lib/xulrunner then replace it with the path that the find command returned.
if it cannot be found at all (with the find command) then maybe its not installed..
try   sudo apt-get install firefox

(in reality anything that installs the libgtkembedmoz.so file is all thats needed to be installed..  this might include only installing xulrunner)


lastly, if you want to run dissent without the exporting LD_LIBRARY_PATH everytime then add the path that contains the file to the */etc/ld.so.conf* file

i hope this helps.
in the future i am looking to get rid of this problem completely.

thanks
goran

---

### Post by hang3r on 2007-04-29
Looks promising, any chance you will include some kind of software mixer/equalizer for audio playback? Seems what most good media players seem to lack, that and a non-existent software based mixer that all linux users face makes our sound experience rather poor. For the moment the only media players I use are XMMS based such as audacious not because I like them, rather because they are the only media players with equalizers! (excluding Amarok).

But I like what I see so far, good work.

---

### Post by BLTicklemonster on 2007-04-29
```

bill@bill-desktop:~$ find /usr/lib -name libgtkembedmoz.so
find:/usr/lib/firefox/libgtkembedmoz.so
bill@bill-desktop:~$ export LD_LIBRARY_PATH=/usr/lib/firefox/libgtkembedmoz.so
bill@bill-desktop:~$ dissent

Dissent-CRITICAL **:

System.TypeInitializationException: An exception was thrown by the type initializer for Gecko.WebControl ---> System.DllNotFoundException: /usr/lib/firefox/libgtkembedmoz.so
  at (wrapper managed-to-native) Gecko.WebControl:gtk_moz_embed_get_type ()
  at Gecko.WebControl.get_GType () [0x00000] 
  at GtkSharp.GeckoSharp.ObjectManager.Initialize () [0x00000] 
  at Gecko.WebControl..cctor () [0x00000] --- End of inner exception stack trace ---

  at <0x00000> <unknown method>
  at DissentGtk.NewsWindow..ctor (Glade.XML gxml) [0x00000] 
  at DissentGtk.Dissent..ctor (System.String[] args) [0x00000] 
  at DissentGtk.Dissent.Main (System.String[] args) [0x00000] 
bill@bill-desktop:~$ 
```

Huh. Argh!

? dll ?

How are you other folks getting it running?

NO wait!!!

I did that wrong, here's me trying it right:

```

bill@bill-desktop:~$ export LD_LIBRARY_PATH=/usr/lib/firefox
bill@bill-desktop:~$ dissent

Dissent-CRITICAL **:

System.DllNotFoundException: gdk-x11-2.0
  at (wrapper managed-to-native) Egg.TrayIcon:gdk_x11_display_get_xdisplay (intptr)
  at Egg.TrayIcon.OnRealized () [0x00000] 
  at Gtk.Widget.realized_cb (IntPtr widget) [0x00000] 
  at (wrapper native-to-managed) Gtk.Widget:realized_cb (intptr)
  at <0x00000> <unknown method>
  at (wrapper managed-to-native) Gtk.Widget:gtk_widget_show_all (intptr)
  at Gtk.Widget.ShowAll () [0x00000] 
  at DissentGtk.Widgets.TrayIcon..ctor () [0x00000] 
  at DissentGtk.Dissent..ctor (System.String[] args) [0x00000] 
  at DissentGtk.Dissent.Main (System.String[] args) [0x00000] 
bill@bill-desktop:~$ 

```

---

### Post by gozza11 on 2007-04-30
@ han3r:
getting an equalizer shouldnt be too dificult. I believe that the banshee project already has one. Since its written in C# it should be a matter of simply making it fit to dissent.


@ BLTicklemonster:
hmmm, at least we got rid of the other problem. this one is an odd error message though.
You might need to install the following package  libgtk2.0-dev
this has worked for the program YouTranslate! which has the exact same error message

---

### Post by BLTicklemonster on 2007-04-30
Bingo!

Now if I can only figure out why my machine all of a sudden is acting up. Ubuntu was frozen up. I had to restart it, and grub took forever to load, then I had a blinky (blinking cursor) for ever, then ubuntu loaded, but I have no audio. 

Perfect timing, dangit.

Weird. The machine was playing streamtuner when it locked up. Music was coming out of it. But when I restarted, no sound. So I restarted again, and on a lark I went in to the bios and changed my onboard audio settings from auto to disabled, and booted, and now my sound works. What's up with that? lol

Anyway, great little program you got here, thanks for taking the time to help me find a solution to get it working.

now where do I find the ld.so.conf file?

---

### Post by JT673 on 2007-04-30
Nice, though you might want to make an install script for those nasty buggers...

The UI feels much at home in GNOME, and the browser is pretty good, though I won't switch that quickly...It needs more features, no? :KS

---

### Post by gozza11 on 2007-05-01
the ld.so.conf file can be found in */etc/*
just edit the file to add  **/usr/lib/firefox**  at the end of the document and then run the command  **ldconfig**  as root


@ JT673:
yea i realised too late about the bugs. im redesigning the code so that it doesnt have so many dependencies. i might whip up a quick script or add a howto on the site though.

more features :D
im working on a plugin architecture right now which should allow me (and others) to write simple plugins that add features such as cd burning, ripping, torrent downloading (for podcasts) and anything else that comes to mind :)

although i should concentrate on simpler things like preferences, full screen theatre controls and everything else a basic media player needs.

im glad that this is receiving a warm welcome. some more developers might join in the project which would hopefully speed up its development.

---

### Post by BLTicklemonster on 2007-05-01
Added all that,

include /etc/ld.so.conf.d/*.conf
include /usr/lib/firefox

ran

bill@bill-desktop:~$ sudo ldconfig

bill@bill-desktop:~$
bill@bill-desktop:~$ dissent


and now this!!!

```
System.TypeInitializationException: An exception was thrown by the type initializer for Gecko.WebControl ---> System.DllNotFoundException: /usr/lib/firefox/libgtkembedmoz.so
  at (wrapper managed-to-native) Gecko.WebControl:gtk_moz_embed_get_type ()
  at Gecko.WebControl.get_GType () [0x00000] 
  at GtkSharp.GeckoSharp.ObjectManager.Initialize () [0x00000] 
  at Gecko.WebControl..cctor () [0x00000] --- End of inner exception stack trace ---

  at <0x00000> <unknown method>
  at DissentGtk.NewsWindow..ctor (Glade.XML gxml) [0x00000] 
  at DissentGtk.Dissent..ctor (System.String[] args) [0x00000] 
  at DissentGtk.Dissent.Main (System.String[] args) [0x00000] 
```

Wheeee.

Perhaps, /firefox/*.so ?

*edit: NO!!! lol

---

### Post by gozza11 on 2007-05-02
its the same error as you originally had. it didnt find the library which indicates that it wasnt entered into the ld.so.conf file properly.

im pretty sure the problem is because you added in 'include'
just add the line** /usr/lib/firefox**  _not_  **include /usr/lib/firefox**

this is what i have got in my ld.so.conf file

------------------------  ld.so.conf ----------------------
/lib
/usr/lib
/usr/local/lib

include /etc/ld.so.conf.d/*.conf

---

### Post by BLTicklemonster on 2007-05-02
:) heh heh heh got it.

So I guess the browser attached is so people can find streaming audio and podcasts and such without leaving the program? No way to make the streams section where it looks them up for you, is there? Or is that a plugin?

---

### Post by gozza11 on 2007-05-02
yea, right now the streams section is a bit under-developed.
you do have a good idea though. everything will be in the form of a plugin to make it easier to develop, so dont be suprised if you see it the next version.

the browser was mainly to make it more convenient. not only to find new podcasts, streams and rss feeds but also to view the podcast website and the full version of the rss news item simply by switching tabs automatically.

since the browser dependency was already there for the rss/podcast preview i figured that i might as well put in a browser, even if its a mundane one

---

### Post by slimdog360 on 2007-05-02
it looks good, I'll have to try it out when I get the chance.

---

### Post by starlightiks on 2007-05-02
```
Unhandled Exception: System.Exception: Unable to open the session message bus. ---> Mono.Unix.UnixIOException: Broken pipe [EPIPE].
  at Mono.Unix.UnixMarshal.ThrowExceptionForLastError () [0x00000] 
  at Mono.Unix.UnixStream.Write (System.Byte[] buffer, Int32 offset, Int32 count) [0x00000] 
  at NDesk.DBus.Connection.WriteMessage (NDesk.DBus.Message msg) [0x00000] 
  at NDesk.DBus.Connection.Send (NDesk.DBus.Message msg) [0x00000] 
  at NDesk.DBus.Connection.SendWithReply (NDesk.DBus.Message msg) [0x00000] 
  at NDesk.DBus.Connection.SendWithReplyAndBlock (NDesk.DBus.Message msg) [0x00000] 
  at NDesk.DBus.BusObject.Invoke (System.Reflection.MethodBase methodBase, System.String methodName, System.Object[] inArgs, System.Object[] outArgs, System.Object retVal, System.Exception exception) [0x00000] 
  at NDesk.DBus.DProxy.Invoke (IMessage message) [0x00000] 
  at System.Runtime.Remoting.Proxies.RealProxy.PrivateInvoke (System.Runtime.Remoting.Proxies.RealProxy rp, IMessage msg, System.Exception exc, System.Object[] out_args) [0x00000] --- End of inner exception stack trace ---

  at NDesk.DBus.Bus.get_Session () [0x00000] 
  at DissentGtk.Remote.GetInstance () [0x00000] 
  at DissentGtk.Dissent..ctor (System.String[] args) [0x00000] 
  at DissentGtk.Dissent.Main (System.String[] args) [0x00000] 
```

I installed it with some problems, but i still got that. But finally if i started it wanted plugins. I put continu or was it close and then it crashed by clicking on any button and gave me a error. What now?

---

### Post by BLTicklemonster on 2007-05-02
It runs, all right, but I do get this message in the terminal:

bill@bill-desktop:~$ dissent
```

(DissentGtk.exe:8521): GLib-GObject-WARNING **: value "0.000000" of type `gfloat' is invalid or out of range for property `ratio' of type `gfloat'

(DissentGtk.exe:8521): GLib-GObject-WARNING **: value "0.000000" of type `gfloat' is invalid or out of range for property `ratio' of type `gfloat'
```

I know you're working out the bugs and stuff, I hope that's helpful.

Great job, btw, and thanks for your help in getting it going.

---

### Post by castironpants on 2007-05-03
Using this guide, I got the program to start up. Unfortunately, it says that there's no media engine. It says to go to the plugins menu, but there are no options on the drop-down menu. The preference menu is also greyed out.

EDIT: Well, it was working...

Now I get:

[email]root@box:/home/jeremy/.diss[/email]ent/dissent-0.1# dissent

Unhandled Exception: System.Exception: Unable to open the session message bus. ---> Mono.Unix.UnixIOException: Broken pipe [EPIPE].
  at Mono.Unix.UnixMarshal.ThrowExceptionForLastError () [0x00000] 
  at Mono.Unix.UnixStream.Write (System.Byte[] buffer, Int32 offset, Int32 count) [0x00000] 
  at NDesk.DBus.Connection.WriteMessage (NDesk.DBus.Message msg) [0x00000] 
  at NDesk.DBus.Connection.Send (NDesk.DBus.Message msg) [0x00000] 
  at NDesk.DBus.Connection.SendWithReply (NDesk.DBus.Message msg) [0x00000] 
  at NDesk.DBus.Connection.SendWithReplyAndBlock (NDesk.DBus.Message msg) [0x00000] 
  at NDesk.DBus.BusObject.Invoke (System.Reflection.MethodBase methodBase, System.String methodName, System.Object[] inArgs, System.Object[]& outArgs, System.Object& retVal, System.Exception& exception) [0x00000] 
  at NDesk.DBus.DProxy.Invoke (IMessage message) [0x00000] 
  at System.Runtime.Remoting.Proxies.RealProxy.PrivateInvoke (System.Runtime.Remoting.Proxies.RealProxy rp, IMessage msg, System.Exception& exc, System.Object[]& out_args) [0x00000] --- End of inner exception stack trace ---

  at NDesk.DBus.Bus.get_Session () [0x00000] 
  at DissentGtk.Remote.GetInstance () [0x00000] 
  at DissentGtk.Dissent..ctor (System.String[] args) [0x00000] 
  at DissentGtk.Dissent.Main (System.String[] args) [0x00000]

---

### Post by gozza11 on 2007-05-04
Unhandled Exception: System.Exception: Unable to open the session message bus. ---> Mono.Unix.UnixIOException: Broken pipe [EPIPE].
......

try running the hal daemon first.
sudo /usr/sbin/hald


castironpants:
did you compile the program or just installed the binary package?
if you just installed the package then have you also installed the dissent-gstreamer package also?

in short it needs the  libdissent_gst.dll  and  libdissent_gst.info  in the plugins folder of where the application is installed. most likely it would be in  /usr/lib/dissent/plugins  or  /usr/local/lib/dissent/plugins

---

### Post by castironpants on 2007-05-04
[By now you've realized I'm very new to Linux] I used the mv command instead of cp. Now it's in BOTH folders and it works. I still can't access preferences though. Not a dire problem, but something to look into...

---

### Post by hanzomon4 on 2007-05-04
I compiled the program and plugin but I get this error message when I attempt to run the program:```
ystem.DllNotFoundException: dissent_gst
  at (wrapper managed-to-native) DissentGstreamer.Engine:gst_binding_init (ulong)
  at DissentGstreamer.Engine.Initiate (UInt64 window_id) [0x00000] 
  at Dissent.Plugin.MediaEngine.Initiate (UInt64 window_id) [0x00000] 
  at Dissent.Plugin.MediaEngine.Load (UInt64 window_id) [0x00000] 
  at DissentGtk.Controls.CreateEngine () [0x00000] 
  at DissentGtk.Dissent.on_mPlugins_activate (System.Object o, System.EventArgs args) [0x00000] 
  at (wrapper delegate-invoke) System.MulticastDelegate:invoke_void_object_EventArgs (object,System.EventArgs)
  at GLib.Signal.voidObjectCallback (IntPtr handle, IntPtr gch) [0x00000] 
  at (wrapper native-to-managed) GLib.Signal:voidObjectCallback (intptr,intptr)
  at <0x00000> <unknown method>
  at (wrapper managed-to-native) Gtk.MenuItem:gtk_menu_item_activate (intptr)
  at Gtk.MenuItem.Activate () [0x00000] 
  at DissentGtk.Dissent..ctor (System.String[] args) [0x00000] 
  at DissentGtk.Dissent.Main (System.String[] args) [0x00000] 
```

It runs when I remove the gstreamer plugin, but obviously can't play anything.

EDIT: I tried running the program and then installing the plugin and selecting it in the plugins menu. It crashed the program

---

### Post by castironpants on 2007-05-04
Ok, so now that I've got it working, I have to say it's a GREAT program. There are one or two things I'd like to see changed though. First, the RSS reader. Back when I used Windows, there was an amazing aggregator called GreatNews. The thing that was so great about it, compared to other readers, was that you could read all your stories at once. Here's an example:

[img]http://images.betanews.com/screenshots/scaled/1130813301-1.jpg[/img]


Instead of having to choose your stories from a list, you had them all presented to you, like a newspaper. The other thing is a very optional add-on. I currently use a great applet called OnTV, which uses XMLTV to give you TV listings. Could something like this be done in Dissent?

EDIT: AHH, other problem! I use RSS to get comic strips, but I can't save them using Dissent. I don't get the right-click menu in the pane! It also doesn't have foward/back buttons!

---

### Post by gozza11 on 2007-05-05
@hanzomon4:
the gstreamer binding library cant be found. it is installed with the gstreamer plugin, the file called libdissent_gst.so, and it will most likely be in  /usr/local/lib  or  /usr/lib

make sure that the file is in one of those directories. if it is and your still getting this error then try adding /usr/local/lib  (or /usr/lib, whichever folder it is in)  to the  ld.so.conf  file and then run the command  ldconfig. (both as root). its basically the same process as i explained earlier but with a different file, see the first page.


@castironpants:
that is a really good idea. i am currently working on the new version of dissent which makes everything modular and expect to see the same feature that GreatNews has :D
since the next version will be plugin based it shouldnt be hard to get something like OnTv working. i use xmltv for my htpc also so it shouldnt take long.

as for the saving images.. its still just a basic browser. it shouldnt be difficult to get more features such as a simple right click menu but it has to be done in a way so as not to exclude the windows version.

"a great program"  :D   thanks!

---

### Post by gozza11 on 2007-07-05
Just an update.

The program is being re-engineered since the first design was clunky and allowed for easy errors to occur.
Now its a more modular design.


The News plugin now displays all the items within a html template similar to what castironpants suggested but with far less features than GreatNews


The SVN version is stable enough for general use so long as you only use the Library and News plugins

svn co [https://dissent.svn.sourceforge.net/svnroot/dissent/trunk](https://dissent.svn.sourceforge.net/svnroot/dissent/trunk) dissent

---

