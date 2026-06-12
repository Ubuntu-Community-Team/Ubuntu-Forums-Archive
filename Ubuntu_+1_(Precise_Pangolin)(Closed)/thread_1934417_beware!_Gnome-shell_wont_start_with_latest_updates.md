---
title: "beware! Gnome-shell wont start with latest updates"
date: 2012-03-02
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by bmbaker on 2012-03-02
latest update from ricotz/testing ppa gnome-shell and gnome-session fallback are not loading! mutter seems ok thhough! if you have synapse installed you can still open a terminal etc!

---

### Post by kansasnoob on 2012-03-02
I'm not even using any ppa's and the latest updates kill gnome-panel :(

---

### Post by ricotz on 2012-03-02
> **bmbaker said:**
> latest update from ricotz/testing ppa gnome-shell and gnome-session fallback are not loading! mutter seems ok thhough! if you have synapse installed you can still open a terminal etc!

A bit more information about the package versions you are using would be useful. Also some kind of crashlog or backtrace would be helpful. 
Although I can't confirm this and it could be related to another updated package which were a lot today btw.

---

### Post by magneze on 2012-03-02
> **ricotz said:**
> A bit more information about the package versions you are using would be useful. Also some kind of crashlog or backtrace would be helpful. 
Although I can't confirm this and it could be related to another updated package which were a lot today btw.I also have this issue. Where should I look for the interesting logs?

The symptoms I get are no top bar, I can just see my desktop background.

Unity still works. I'm now reminded why I switched to Gnome Shell and I want it back! :)

---

### Post by ricotz on 2012-03-02
> **magneze said:**
> I also have this issue. Where should I look for the interesting logs?

The symptoms I get are no top bar, I can just see my desktop background.

Unity still works. I'm now reminded why I switched to Gnome Shell and I want it back! :)

The simplest to begin with would be to mention the package versions using something like "dpkg -l gnome-shell mutter libgjs0c libclutter-1.0-0 libcogl8" (in case of g-s failing with ppa:ricotz/testing or ppa:gnome3-team/ppa) 
Some logged errors you can find in ~/.xsession-errors (where you need to look at after you tried to start the session, you must not start another "working" session before looking at this file) 
More complicated would be to get a backtrace which you can do using gdb.

---

### Post by tista on 2012-03-02
Hi guys,

I've seen this log on my .xsession-errors on gnome-fallback session (especially I've never seen before...):

```
gnome-session[1610]: WARNING: Application 'gsettings-data-convert.desktop' kille
d by signal
gnome-session[1610]: WARNING: App 'gsettings-data-convert.desktop' respawning to
o quickly
gnome-session[1610]: WARNING: Error on restarting session managed app: Component
 'gsettings-data-convert.desktop' crashing too quickly
```

And now I'm using these versions:

```
ii  gnome-shell    3.3.90+git2012 graphical shell for the GNOME desktop
ii  libclutter-1.0 1.9.13+git2012 Open GL based interactive canvas library
ii  libcogl8       1.9.7+git20120 Object oriented GL/GLES Abstraction/Utility 
ii  libgjs0c       1.31.10+git201 Mozilla-based javascript bindings for the GN
ii  mutter         3.3.90+git2012 lightweight GTK+ window manager
```

Cheers,
Tista

P.S:
I've experienced some interesting issue... on gtk3 applications, the GtkMenus seems to be ignored "hover/prelight" statements by covering mouse pointer accross over these items. X( but gtk2 apps seems OK. So I have to click menuitems to show sub-menus...

---

### Post by Quackers on 2012-03-02
After running the latest updates gnome-shell does not start - it seems to try to start but then defaults to unity, which starts fine.
I'm not using ricotz ppa, this is a bog standard gnome-shell setup (if that's possible :-) ).

---

### Post by sgage on 2012-03-02
> **kansasnoob said:**
> I'm not even using any ppa's and the latest updates kill gnome-panel :(

No ppa's here either, and neither gnome shell nor gnome fallback have any panels. It appears that nautilus is running - a right-click on the desktop brings up the appropriate context menu.

---

### Post by tista on 2012-03-02
And now I've tried to run gnome-shell via "gnome-shell --replace" on terminal kicked in gnome-fallback session:

below is the fully log:
[http://paste.ubuntu.com/865195/]("http://paste.ubuntu.com/865195/")
I hope this could help the devs... ;)

P.S:
"gnome-shell --replace" could run gs normally... ??? what happened?
But anyway my gdm 3.2.1 also died... OMG... :(

---

### Post by bmbaker on 2012-03-02
you can run G-S still from the terminal with gnome-shell --replace
here is the output of the ./xsession-errors
and the terminal output after gnome-shell --replace
I am running all the latest versions fro the ricotz/testing ppa



```
/usr/sbin/lightdm-session: 65: /etc/X11/Xsession.d/20x11-common_process-args: message: not found

color-plugin-WARNING **: failed to get edid: unable to get EDID for output
Backend     : gconf
Integration : true
Profile     : default
Adding plugins
Initializing core options...done
x-session-manager[3904]: WARNING: Application 'compiz.desktop' failed to register before timeout
x-session-manager[3904]: CRITICAL: We failed, but the fail whale is dead. Sorry....
** Message: applet now removed from the notification area
** Message: using fallback from indicator to GtkStatusIcon

** WARNING **: Trying to register gtype 'GMountMountFlags' as enum when in fact it is of type 'GFlags'

** WARNING **: Trying to register gtype 'GDriveStartFlags' as enum when in fact it is of type 'GFlags'
x-session-manager[3904]: WARNING: Could not launch application 'gdu-notification-daemon.desktop': Unable to start application: Failed to execute child process "/usr/lib/gnome-disk-utility/gdu-notification-daemon" (No such file or directory)
Initializing composite options...done
Initializing opengl options...done
Initializing decor options...done
Initializing vpswitch options...done
Initializing snap options...done
Initializing mousepoll options...done
Initializing resize options...done
Initializing place options...done
Initializing move options...done
Initializing wall options...done
Initializing grid options...done
I/O warning : failed to load external entity "/home/bb/.compiz/session/10b47155e96524fd4a133070033284551400000039040051"
Initializing session options...done
Initializing gnomecompat options...done
Initializing animation options...done
Initializing fade options...done
Initializing unitymtgrabhandles options...done
Initializing workarounds options...done
Initializing scale options...done
compiz (expo) - Warn: failed to bind image to texture
Initializing expo options...done
Initializing ezoom options...done
Initializing staticswitcher options...done
Initializing unityshell options...done
Setting Update "main_menu_key"
Setting Update "run_key"
Setting Update "main_menu_key"
Setting Update "run_key"

** WARNING **: zeitgeist-datahub.vala:224: Unable to get name "org.gnome.zeitgeist.datahub" on the bus!
Discarding: 8 over 9
Discarding: 5 over 9

** CRITICAL **: nautilus_menu_provider_get_background_items: assertion `NAUTILUS_IS_MENU_PROVIDER (provider)' failed

** CRITICAL **: nautilus_menu_provider_get_background_items: assertion `NAUTILUS_IS_MENU_PROVIDER (provider)' failed

** CRITICAL **: nautilus_menu_provider_get_background_items: assertion `NAUTILUS_IS_MENU_PROVIDER (provider)' failed

** CRITICAL **: nautilus_menu_provider_get_background_items: assertion `NAUTILUS_IS_MENU_PROVIDER (provider)' failed

** CRITICAL **: nautilus_menu_provider_get_background_items: assertion `NAUTILUS_IS_MENU_PROVIDER (provider)' failed

** CRITICAL **: nautilus_menu_provider_get_background_items: assertion `NAUTILUS_IS_MENU_PROVIDER (provider)' failed

** CRITICAL **: nautilus_menu_provider_get_background_items: assertion `NAUTILUS_IS_MENU_PROVIDER (provider)' failed

** CRITICAL **: nautilus_menu_provider_get_background_items: assertion `NAUTILUS_IS_MENU_PROVIDER (provider)' failed

** CRITICAL **: nautilus_menu_provider_get_background_items: assertion `NAUTILUS_IS_MENU_PROVIDER (provider)' failed

** CRITICAL **: nautilus_menu_provider_get_background_items: assertion `NAUTILUS_IS_MENU_PROVIDER (provider)' failed

** CRITICAL **: nautilus_menu_provider_get_background_items: assertion `NAUTILUS_IS_MENU_PROVIDER (provider)' failed

** CRITICAL **: nautilus_menu_provider_get_file_items: assertion `NAUTILUS_IS_MENU_PROVIDER (provider)' failed

** CRITICAL **: nautilus_menu_item_list_free: assertion `item_list != NULL' failed

** CRITICAL **: nautilus_menu_item_list_free: assertion `item_list != NULL' failed

** CRITICAL **: nautilus_menu_item_list_free: assertion `item_list != NULL' failed

** CRITICAL **: nautilus_menu_provider_get_file_items: assertion `NAUTILUS_IS_MENU_PROVIDER (provider)' failed

** CRITICAL **: nautilus_menu_item_list_free: assertion `item_list != NULL' failed

** CRITICAL **: nautilus_menu_item_list_free: assertion `item_list != NULL' failed

** CRITICAL **: nautilus_menu_item_list_free: assertion `item_list != NULL' failed

** CRITICAL **: nautilus_menu_provider_get_file_items: assertion `NAUTILUS_IS_MENU_PROVIDER (provider)' failed

** CRITICAL **: nautilus_menu_item_list_free: assertion `item_list != NULL' failed

** CRITICAL **: nautilus_menu_item_list_free: assertion `item_list != NULL' failed

** CRITICAL **: nautilus_menu_item_list_free: assertion `item_list != NULL' failed

** CRITICAL **: nautilus_menu_provider_get_file_items: assertion `NAUTILUS_IS_MENU_PROVIDER (provider)' failed

** CRITICAL **: nautilus_menu_item_list_free: assertion `item_list != NULL' failed

** CRITICAL **: nautilus_menu_item_list_free: assertion `item_list != NULL' failed

** CRITICAL **: nautilus_menu_item_list_free: assertion `item_list != NULL' failed

** CRITICAL **: nautilus_menu_provider_get_file_items: assertion `NAUTILUS_IS_MENU_PROVIDER (provider)' failed

** CRITICAL **: nautilus_menu_item_list_free: assertion `item_list != NULL' failed

** CRITICAL **: nautilus_menu_item_list_free: assertion `item_list != NULL' failed

** CRITICAL **: nautilus_menu_item_list_free: assertion `item_list != NULL' failed

** CRITICAL **: nautilus_menu_provider_get_file_items: assertion `NAUTILUS_IS_MENU_PROVIDER (provider)' failed

** CRITICAL **: nautilus_menu_item_list_free: assertion `item_list != NULL' failed

** CRITICAL **: nautilus_menu_item_list_free: assertion `item_list != NULL' failed

** CRITICAL **: nautilus_menu_item_list_free: assertion `item_list != NULL' failed

** CRITICAL **: nautilus_menu_provider_get_background_items: assertion `NAUTILUS_IS_MENU_PROVIDER (provider)' failed

** CRITICAL **: nautilus_menu_provider_get_background_items: assertion `NAUTILUS_IS_MENU_PROVIDER (provider)' failed

** CRITICAL **: nautilus_menu_provider_get_background_items: assertion `NAUTILUS_IS_MENU_PROVIDER (provider)' failed

** CRITICAL **: nautilus_menu_provider_get_background_items: assertion `NAUTILUS_IS_MENU_PROVIDER (provider)' failed

** CRITICAL **: nautilus_menu_provider_get_background_items: assertion `NAUTILUS_IS_MENU_PROVIDER (provider)' failed

** CRITICAL **: nautilus_menu_provider_get_background_items: assertion `NAUTILUS_IS_MENU_PROVIDER (provider)' failed

** CRITICAL **: nautilus_menu_provider_get_background_items: assertion `NAUTILUS_IS_MENU_PROVIDER (provider)' failed

** CRITICAL **: nautilus_menu_provider_get_background_items: assertion `NAUTILUS_IS_MENU_PROVIDER (provider)' failed

** CRITICAL **: nautilus_menu_provider_get_background_items: assertion `NAUTILUS_IS_MENU_PROVIDER (provider)' failed

** CRITICAL **: nautilus_menu_provider_get_background_items: assertion `NAUTILUS_IS_MENU_PROVIDER (provider)' failed

** CRITICAL **: nautilus_menu_provider_get_background_items: assertion `NAUTILUS_IS_MENU_PROVIDER (provider)' failed

** CRITICAL **: nautilus_menu_provider_get_file_items: assertion `NAUTILUS_IS_MENU_PROVIDER (provider)' failed

** CRITICAL **: nautilus_menu_item_list_free: assertion `item_list != NULL' failed

** CRITICAL **: nautilus_menu_item_list_free: assertion `item_list != NULL' failed

** CRITICAL **: nautilus_menu_item_list_free: assertion `item_list != NULL' failed

** CRITICAL **: nautilus_menu_provider_get_file_items: assertion `NAUTILUS_IS_MENU_PROVIDER (provider)' failed

** CRITICAL **: nautilus_menu_item_list_free: assertion `item_list != NULL' failed

** CRITICAL **: nautilus_menu_item_list_free: assertion `item_list != NULL' failed

** CRITICAL **: nautilus_menu_provider_get_file_items: assertion `NAUTILUS_IS_MENU_PROVIDER (provider)' failed

** CRITICAL **: nautilus_menu_item_list_free: assertion `item_list != NULL' failed

** CRITICAL **: nautilus_menu_item_list_free: assertion `item_list != NULL' failed

** CRITICAL **: nautilus_menu_provider_get_background_items: assertion `NAUTILUS_IS_MENU_PROVIDER (provider)' failed

** CRITICAL **: nautilus_menu_provider_get_background_items: assertion `NAUTILUS_IS_MENU_PROVIDER (provider)' failed

** CRITICAL **: nautilus_menu_provider_get_background_items: assertion `NAUTILUS_IS_MENU_PROVIDER (provider)' failed

** CRITICAL **: nautilus_menu_provider_get_background_items: assertion `NAUTILUS_IS_MENU_PROVIDER (provider)' failed

** CRITICAL **: nautilus_menu_provider_get_background_items: assertion `NAUTILUS_IS_MENU_PROVIDER (provider)' failed

** CRITICAL **: nautilus_menu_provider_get_background_items: assertion `NAUTILUS_IS_MENU_PROVIDER (provider)' failed

** CRITICAL **: nautilus_menu_provider_get_background_items: assertion `NAUTILUS_IS_MENU_PROVIDER (provider)' failed

** CRITICAL **: nautilus_menu_provider_get_background_items: assertion `NAUTILUS_IS_MENU_PROVIDER (provider)' failed

** CRITICAL **: nautilus_menu_provider_get_background_items: assertion `NAUTILUS_IS_MENU_PROVIDER (provider)' failed

** CRITICAL **: nautilus_menu_provider_get_background_items: assertion `NAUTILUS_IS_MENU_PROVIDER (provider)' failed

** CRITICAL **: nautilus_menu_provider_get_background_items: assertion `NAUTILUS_IS_MENU_PROVIDER (provider)' failed

** CRITICAL **: nautilus_menu_provider_get_file_items: assertion `NAUTILUS_IS_MENU_PROVIDER (provider)' failed

** CRITICAL **: nautilus_menu_item_list_free: assertion `item_list != NULL' failed

** CRITICAL **: nautilus_menu_item_list_free: assertion `item_list != NULL' failed

** CRITICAL **: nautilus_menu_item_list_free: assertion `item_list != NULL' failed

** CRITICAL **: nautilus_menu_provider_get_file_items: assertion `NAUTILUS_IS_MENU_PROVIDER (provider)' failed

** CRITICAL **: nautilus_menu_item_list_free: assertion `item_list != NULL' failed

** CRITICAL **: nautilus_menu_item_list_free: assertion `item_list != NULL' failed

** CRITICAL **: nautilus_menu_item_list_free: assertion `item_list != NULL' failed

** CRITICAL **: nautilus_menu_provider_get_background_items: assertion `NAUTILUS_IS_MENU_PROVIDER (provider)' failed

** CRITICAL **: nautilus_menu_provider_get_background_items: assertion `NAUTILUS_IS_MENU_PROVIDER (provider)' failed

** CRITICAL **: nautilus_menu_provider_get_background_items: assertion `NAUTILUS_IS_MENU_PROVIDER (provider)' failed

** CRITICAL **: nautilus_menu_provider_get_background_items: assertion `NAUTILUS_IS_MENU_PROVIDER (provider)' failed

** CRITICAL **: nautilus_menu_provider_get_background_items: assertion `NAUTILUS_IS_MENU_PROVIDER (provider)' failed

** CRITICAL **: nautilus_menu_provider_get_background_items: assertion `NAUTILUS_IS_MENU_PROVIDER (provider)' failed

** CRITICAL **: nautilus_menu_provider_get_background_items: assertion `NAUTILUS_IS_MENU_PROVIDER (provider)' failed

** CRITICAL **: nautilus_menu_provider_get_background_items: assertion `NAUTILUS_IS_MENU_PROVIDER (provider)' failed

** CRITICAL **: nautilus_menu_provider_get_background_items: assertion `NAUTILUS_IS_MENU_PROVIDER (provider)' failed

** CRITICAL **: nautilus_menu_provider_get_background_items: assertion `NAUTILUS_IS_MENU_PROVIDER (provider)' failed

** CRITICAL **: nautilus_menu_provider_get_background_items: assertion `NAUTILUS_IS_MENU_PROVIDER (provider)' failed

** CRITICAL **: nautilus_menu_provider_get_file_items: assertion `NAUTILUS_IS_MENU_PROVIDER (provider)' failed

** CRITICAL **: nautilus_menu_item_list_free: assertion `item_list != NULL' failed

** CRITICAL **: nautilus_menu_item_list_free: assertion `item_list != NULL' failed

** CRITICAL **: nautilus_menu_item_list_free: assertion `item_list != NULL' failed

** CRITICAL **: nautilus_menu_provider_get_file_items: assertion `NAUTILUS_IS_MENU_PROVIDER (provider)' failed

** CRITICAL **: nautilus_menu_item_list_free: assertion `item_list != NULL' failed

** CRITICAL **: nautilus_menu_item_list_free: assertion `item_list != NULL' failed

** CRITICAL **: nautilus_menu_provider_get_file_items: assertion `NAUTILUS_IS_MENU_PROVIDER (provider)' failed

** CRITICAL **: nautilus_menu_item_list_free: assertion `item_list != NULL' failed

** CRITICAL **: nautilus_menu_item_list_free: assertion `item_list != NULL' failed

** CRITICAL **: nautilus_menu_provider_get_background_items: assertion `NAUTILUS_IS_MENU_PROVIDER (provider)' failed

** CRITICAL **: nautilus_menu_provider_get_background_items: assertion `NAUTILUS_IS_MENU_PROVIDER (provider)' failed

** CRITICAL **: nautilus_menu_provider_get_background_items: assertion `NAUTILUS_IS_MENU_PROVIDER (provider)' failed

** CRITICAL **: nautilus_menu_provider_get_background_items: assertion `NAUTILUS_IS_MENU_PROVIDER (provider)' failed

** CRITICAL **: nautilus_menu_provider_get_background_items: assertion `NAUTILUS_IS_MENU_PROVIDER (provider)' failed

** CRITICAL **: nautilus_menu_provider_get_background_items: assertion `NAUTILUS_IS_MENU_PROVIDER (provider)' failed

** CRITICAL **: nautilus_menu_provider_get_background_items: assertion `NAUTILUS_IS_MENU_PROVIDER (provider)' failed

** CRITICAL **: nautilus_menu_provider_get_background_items: assertion `NAUTILUS_IS_MENU_PROVIDER (provider)' failed

** CRITICAL **: nautilus_menu_provider_get_background_items: assertion `NAUTILUS_IS_MENU_PROVIDER (provider)' failed

** CRITICAL **: nautilus_menu_provider_get_background_items: assertion `NAUTILUS_IS_MENU_PROVIDER (provider)' failed

** CRITICAL **: nautilus_menu_provider_get_background_items: assertion `NAUTILUS_IS_MENU_PROVIDER (provider)' failed

** CRITICAL **: nautilus_menu_provider_get_file_items: assertion `NAUTILUS_IS_MENU_PROVIDER (provider)' failed

** CRITICAL **: nautilus_menu_item_list_free: assertion `item_list != NULL' failed

** CRITICAL **: nautilus_menu_item_list_free: assertion `item_list != NULL' failed

** CRITICAL **: nautilus_menu_item_list_free: assertion `item_list != NULL' failed

** CRITICAL **: nautilus_menu_provider_get_file_items: assertion `NAUTILUS_IS_MENU_PROVIDER (provider)' failed

** CRITICAL **: nautilus_menu_item_list_free: assertion `item_list != NULL' failed

** CRITICAL **: nautilus_menu_item_list_free: assertion `item_list != NULL' failed

** CRITICAL **: nautilus_menu_item_list_free: assertion `item_list != NULL' failed

** CRITICAL **: nautilus_menu_provider_get_file_items: assertion `NAUTILUS_IS_MENU_PROVIDER (provider)' failed

** CRITICAL **: nautilus_menu_item_list_free: assertion `item_list != NULL' failed

** CRITICAL **: nautilus_menu_item_list_free: assertion `item_list != NULL' failed

** CRITICAL **: nautilus_menu_item_list_free: assertion `item_list != NULL' failed

** CRITICAL **: nautilus_menu_provider_get_file_items: assertion `NAUTILUS_IS_MENU_PROVIDER (provider)' failed

** CRITICAL **: nautilus_menu_item_list_free: assertion `item_list != NULL' failed

** CRITICAL **: nautilus_menu_item_list_free: assertion `item_list != NULL' failed

** CRITICAL **: nautilus_menu_item_list_free: assertion `item_list != NULL' failed

** CRITICAL **: nautilus_menu_provider_get_file_items: assertion `NAUTILUS_IS_MENU_PROVIDER (provider)' failed

** CRITICAL **: nautilus_menu_item_list_free: assertion `item_list != NULL' failed

** CRITICAL **: nautilus_menu_item_list_free: assertion `item_list != NULL' failed

** CRITICAL **: nautilus_menu_item_list_free: assertion `item_list != NULL' failed
THREAD>>>>   Update months events around: March 2012 | months_back 12 | months_ahead 12
      <<<<THREAD>>>>   Getting events from brian baker ...
      <<<<THREAD>>>>   Getting events from Küchen-Team ...
      <<<<THREAD>>>>   Getting events from German Holidays ...
      <<<<THREAD>>>>   Getting events from Kossin works ...
      <<<<THREAD>>>>   #Updated events since March 2011 until March 2013
Checking if actual month events need update...
No need for update
Checking if actual month events need update...
No need for update
Checking if actual month events need update...
Scheduler starts updater thread...
      <<<<THREAD>>>>   Update months events around: March 2012 | months_back 12 | months_ahead 12
      <<<<THREAD>>>>   Getting events from brian baker ...
      <<<<THREAD>>>>   Getting events from Küchen-Team ...
      <<<<THREAD>>>>   Getting events from German Holidays ...
      <<<<THREAD>>>>   Getting events from Kossin works ...
      <<<<THREAD>>>>   #Updated events since March 2011 until March 2013
Checking if actual month events need update...
No need for update
Checking if actual month events need update...
No need for update
Checking if actual month events need update...
Scheduler starts updater thread...
      <<<<THREAD>>>>   Update months events around: March 2012 | months_back 12 | months_ahead 12
      <<<<THREAD>>>>   Getting events from brian baker ...
      <<<<THREAD>>>>   Getting events from Küchen-Team ...
      <<<<THREAD>>>>   Getting events from German Holidays ...
      <<<<THREAD>>>>   Getting events from Kossin works ...
      <<<<THREAD>>>>   #Updated events since March 2011 until March 2013
Checking if actual month events need update...
No need for update
Checking if actual month events need update...
No need for update
Checking if actual month events need update...
Scheduler starts updater thread...
      <<<<THREAD>>>>   Update months events around: March 2012 | months_back 12 | months_ahead 12
      <<<<THREAD>>>>   Getting events from brian baker ...
      <<<<THREAD>>>>   Getting events from Küchen-Team ...
      <<<<THREAD>>>>   Getting events from German Holidays ...
      <<<<THREAD>>>>   Getting events from Kossin works ...
      <<<<THREAD>>>>   #Updated events since March 2011 until March 2013
Checking if actual month events need update...
No need for update
Checking if actual month events need update...
No need for update
Checking if actual month events need update...
Scheduler starts updater thread...
      <<<<THREAD>>>>   Update months events around: March 2012 | months_back 12 | months_ahead 12
    Traceback (most recent call last):
  File "/usr/lib/python2.7/dist-packages/turpial/api/protocols/twitter/http.py", line 128, in request
    rtn = self.do_request(uri, args)
  File "/usr/lib/python2.7/dist-packages/turpial/api/interfaces/http.py", line 186, in do_request
    response = self.__send(authreq)
  File "/usr/lib/python2.7/dist-packages/turpial/api/interfaces/http.py", line 158, in __send
    handle = urllib2.urlopen(req)
  File "/usr/lib/python2.7/urllib2.py", line 126, in urlopen
    return _opener.open(url, data, timeout)
  File "/usr/lib/python2.7/urllib2.py", line 406, in open
    response = meth(req, response)
  File "/usr/lib/python2.7/urllib2.py", line 519, in http_response
    'http', request, response, code, msg, hdrs)
  File "/usr/lib/python2.7/urllib2.py", line 444, in error
    return self._call_chain(*args)
  File "/usr/lib/python2.7/urllib2.py", line 378, in _call_chain
    result = func(*args)
  File "/usr/lib/python2.7/urllib2.py", line 527, in http_error_default
    raise HTTPError(req.get_full_url(), code, msg, hdrs, fp)
HTTPError: HTTP Error 503: Service Unavailable
Window manager warning: Log level 8: meta_window_focus: assertion `!window->override_redirect' failed
Window manager warning: Log level 8: meta_window_focus: assertion `!window->override_redirect' failed
Window manager warning: Log level 8: meta_window_focus: assertion `!window->override_redirect' failed
Window manager warning: Log level 8: meta_window_focus: assertion `!window->override_redirect' failed
  <<<<THREAD>>>>   Getting events from brian baker ...
      <<<<THREAD>>>>   Getting events from Küchen-Team ...
      <<<<THREAD>>>>   Getting events from German Holidays ...
      <<<<THREAD>>>>   Getting events from Kossin works ...
      <<<<THREAD>>>>   #Updated events since March 2011 until March 2013
Checking if actual month events need update...
No need for update
Checking if actual month events need update...
No need for update
Checking if actual month events need update...
Scheduler starts updater thread...
      <<<<THREAD>>>>   Update months events around: March 2012 | months_back 12 | months_ahead 12
      <<<<THREAD>>>>   Getting events from brian baker ...
      <<<<THREAD>>>>   Getting events from Küchen-Team ...
      <<<<THREAD>>>>   Getting events from German Holidays ...
      <<<<THREAD>>>>   Getting events from Kossin works ...
      <<<<THREAD>>>>   #Updated events since March 2011 until March 2013
Checking if actual month events need update...
No need for update
Checking if actual month events need update...
No need for update
Checking if actual month events need update...
Scheduler starts updater thread...
      <<<<THREAD>>>>   Update months events around: March 2012 | months_back 12 | months_ahead 12
      <<<<THREAD>>>>   Getting events from brian baker ...
      <<<<THREAD>>>>   Getting events from Küchen-Team ...
      <<<<THREAD>>>>   Getting events from German Holidays ...
      <<<<THREAD>>>>   Getting events from Kossin works ...
      <<<<THREAD>>>>   #Updated events since March 2011 until March 2013
Checking if actual month events need update...
No need for update
Checking if actual month events need update...
No need for update
Checking if actual month events need update...
Scheduler starts updater thread...
      <<<<THREAD>>>>   Update months events around: March 2012 | months_back 12 | months_ahead 12
      <<<<THREAD>>>>   Getting events from brian baker ...
      <<<<THREAD>>>>   Getting events from Küchen-Team ...
      <<<<THREAD>>>>   Getting events from German Holidays ...
      <<<<THREAD>>>>   Getting events from Kossin works ...
      <<<<THREAD>>>>   #Updated events since March 2011 until March 2013
Checking if actual month events need update...
No need for update
Checking if actual month events need update...
No need for update
Checking if actual month events need update...
Scheduler starts updater thread...
      <<<<THREAD>>>>   Update months events around: March 2012 | months_back 12 | months_ahead 12
      <<<<THREAD>>>>   Getting events from brian baker ...
      <<<<THREAD>>>>   Getting events from Küchen-Team ...
      <<<<THREAD>>>>   Getting events from German Holidays ...
      <<<<THREAD>>>>   Getting events from Kossin works ...
      <<<<THREAD>>>>   #Updated events since March 2011 until March 2013
Checking if actual month events need update...
No need for update
Checking if actual month events need update...
No need for update
Checking if actual month events need update...
Scheduler starts updater thread...
      <<<<THREAD>>>>   Update months events around: March 2012 | months_back 12 | months_ahead 12
      <<<<THREAD>>>>   Getting events from brian baker ...
      <<<<THREAD>>>>   Getting events from Küchen-Team ...
      <<<<THREAD>>>>   Getting events from German Holidays ...
      <<<<THREAD>>>>   Getting events from Kossin works ...
      <<<<THREAD>>>>   #Updated events since March 2011 until March 2013
Checking if actual month events need update...
No need for update
Checking if actual month events need update...
No need for update
Checking if actual month events need update...
Scheduler starts updater thread...
      <<<<THREAD>>>>   Update months events around: March 2012 | months_back 12 | months_ahead 12
      <<<<THREAD>>>>   Getting events from brian baker ...
      <<<<THREAD>>>>   Getting events from Küchen-Team ...
      <<<<THREAD>>>>   Getting events from German Holidays ...
      <<<<THREAD>>>>   Getting events from Kossin works ...
      <<<<THREAD>>>>   #Updated events since March 2011 until March 2013
Checking if actual mont
Cogl-WARNING **: ./driver/gl/cogl-texture-driver-gl.c:274: GL error (1280): Invalid enumeration value


Cogl-WARNING **: ./driver/gl/cogl-texture-driver-gl.c:274: GL error (1280): Invalid enumeration value


Cogl-WARNING **: ./driver/gl/cogl-texture-driver-gl.c:274: GL error (1280): Invalid enumeration value


Cogl-WARNING **: ./driver/gl/cogl-texture-driver-gl.c:274: GL error (1280): Invalid enumeration value


Cogl-WARNING **: ./driver/gl/cogl-texture-driver-gl.c:274: GL error (1280): Invalid enumeration value


Cogl-WARNING **: ./driver/gl/cogl-texture-driver-gl.c:274: GL error (1280): Invalid enumeration value


Cogl-WARNING **: ./driver/gl/cogl-texture-driver-gl.c:274: GL error (1280): Invalid enumeration value


Cogl-WARNING **: ./driver/gl/cogl-texture-driver-gl.c:274: GL error (1280): Invalid enumeration value


Cogl-WARNING **: ./driver/gl/cogl-texture-driver-gl.c:274: GL error (1280): Invalid enumeration value


Cogl-WARNING **: ./driver/gl/cogl-texture-driver-gl.c:274: GL error (1280): Invalid enumeration value


Cogl-WARNING **: ./driver/gl/cogl-texture-driver-gl.c:274: GL error (1280): Invalid enumeration value


Cogl-WARNING **: ./driver/gl/cogl-texture-driver-gl.c:274: GL error (1280): Invalid enumeration value


Cogl-WARNING **: ./driver/gl/cogl-texture-driver-gl.c:274: GL error (1280): Invalid enumeration value


Cogl-WARNING **: ./driver/gl/cogl-texture-driver-gl.c:274: GL error (1280): Invalid enumeration value


Cogl-WARNING **: ./driver/gl/cogl-texture-driver-gl.c:274: GL error (1280): Invalid enumeration value

Window manager warning: Log level 8: meta_window_focus: assertion `!window->override_redirect' failed

Cogl-WARNING **: ./driver/gl/cogl-texture-driver-gl.c:274: GL error (1280): Invalid enumeration value

h events need update...
No need for update
Checking if actual month events need update...
No need for update
Checking if actual month events need update...
Scheduler starts updater thread...
      <<<<THREAD>>>>   Update months events around: March 2012 | months_back 12 | months_ahead 12
      <<<<THREAD>>>>   Getting events from brian baker ...
      <<<<THREAD>>>>   Getting events from Küchen-Team ...
      <<<<THREAD>>>>   Getting events from German Holidays ...
      <<<<THREAD>>>>   Getting events from Kossin works ...
      <<<<THREAD>>>>   #Updated events since March 2011 until March 2013
Checking if actual month events need update...
No need for update
Checking if actual month events need update...
No need for update
Checking if actual month events need update...
Scheduler starts updater thread...
      <<<<THREAD>>>>   Update months events around: March 2012 | months_back 12 | months_ahead 12
      <<<<THREAD>>>>   Getting events from brian baker ...
      <<<<THREAD>>>>   Getting events from Küchen-Team ...
      <<<<THREAD>>>>   Getting events from German Holidays ...
      <<<<THREAD>>>>   Getting events from Kossin works ...
      <<<<THREAD>>>>   #Updated events since March 2011 until March 2013
Checking if actual month events need update...
No need for update
Checking if actual month events need update...
No need for update
Checking if actual month events need update...
Scheduler starts updater thread...
      <<<<THREAD>>>>   Update months events around: March 2012 | months_back 12 | months_ahead 12
      <<<<THREAD>>>>   Getting events from brian baker ...
      <<<<THREAD>>>>   Getting events from Küchen-Team ...
      <<<<THREAD>>>>   Getting events from German Holidays ...
      <<<<THREAD>>>>   Getting events from Kossin works ...
      <<<<THREAD>>>>   #Updated events since March 2011 until March 2013
Checking if actual month events need update...
No need for update
Checking if actual month events need update...
No need for update
Checking if actual month events need update...
Scheduler starts updater thread...
      <<<<THREAD>>>>   Update months events around: March 2012 | months_back 12 | months_ahead 12
      <<<<THREAD>>>>   Getting events from brian baker ...
      <<<<THREAD>>>>   Getting events from Küchen-Team ...
      <<<<THREAD>>>>   Getting events from German Holidays ...
      <<<<THREAD>>>>   Getting events from Kossin works ...
      <<<<THREAD>>>>   #Updated events since March 2011 until March 2013
Checking if actual month events need update...
No need for update
Checking if actual month events need update...
No need for update
Checking if actual month events need update...
Scheduler starts updater thread...
      <<<<THREAD>>>>   Update months events around: March 2012 | months_back 12 | months_ahead 12
      <<<<THREAD>>>>   Getting events from brian baker ...
      <<<<THREAD>>>>   Getting events from Küchen-Team ...
      <<<<THREAD>>>>   Getting events from German Holidays ...
      <<<<THREAD>>>>   Getting events from Kossin works ...
      <<<<THREAD>>>>   #Updated events since March 2011 until March 2013
Checking if actual month events need update...
No need for update
Checking if actual month events need update...
No need for update
Checking if actual month events need update...
Scheduler starts updater thread...
      <<<<THREAD>>>>   Update months events around: March 2012 | months_back 12 | months_ahead 12
      <<<<THREAD>>>>   Getting events from brian baker ...
      <<<<THREAD>>>>   Getting events from Küchen-Team ...
      <<<<THREAD>>>>   Getting events from German Holidays ...
      <<<<THREAD>>>>   Getting events from Kossin works ...
      <<<<THREAD>>>>   #Updated events since March 2011 until March 2013
Checking if actual month events need update...
No need for update
Checking if actual month events need update...
No need for update
Checking if actual month events need update...
Scheduler starts updater thread...
      <<<<THREAD>>>>   Update months events around: March 2012 | months_back 12 | months_ahead 12
      <<<<THREAD>>>>   Getting events from br
Cogl-WARNING **: ./driver/gl/cogl-texture-driver-gl.c:274: GL error (1280): Invalid enumeration value

Window manager warning: Log level 8: g_object_unref: assertion `G_IS_OBJECT (object)' failed
Window manager warning: Log level 8: g_object_unref: assertion `G_IS_OBJECT (object)' failed
Window manager warning: Log level 8: g_object_unref: assertion `G_IS_OBJECT (object)' failed
Window manager warning: Log level 16: invalid (NULL) pointer instance
Window manager warning: Log level 8: g_signal_handler_disconnect: assertion `G_TYPE_CHECK_INSTANCE (instance)' failed

Cogl-WARNING **: ./driver/gl/cogl-texture-driver-gl.c:274: GL error (1280): Invalid enumeration value


Cogl-WARNING **: ./driver/gl/cogl-texture-driver-gl.c:274: GL error (1280): Invalid enumeration value


Cogl-WARNING **: ./driver/gl/cogl-texture-driver-gl.c:274: GL error (1280): Invalid enumeration value


Cogl-WARNING **: ./driver/gl/cogl-texture-driver-gl.c:274: GL error (1280): Invalid enumeration value


Cogl-WARNING **: ./driver/gl/cogl-texture-driver-gl.c:274: GL error (1280): Invalid enumeration value


Cogl-WARNING **: ./driver/gl/cogl-texture-driver-gl.c:274: GL error (1280): Invalid enumeration value


Cogl-WARNING **: ./driver/gl/cogl-texture-driver-gl.c:274: GL error (1280): Invalid enumeration value


Cogl-WARNING **: ./driver/gl/cogl-texture-driver-gl.c:274: GL error (1280): Invalid enumeration value


Cogl-WARNING **: ./driver/gl/cogl-texture-driver-gl.c:274: GL error (1280): Invalid enumeration value


Cogl-WARNING **: ./driver/gl/cogl-texture-driver-gl.c:274: GL error (1280): Invalid enumeration value


Cogl-WARNING **: ./driver/gl/cogl-texture-driver-gl.c:274: GL error (1280): Invalid enumeration value


Cogl-WARNING **: ./driver/gl/cogl-texture-driver-gl.c:274: GL error (1280): Invalid enumeration value


Cogl-WARNING **: ./driver/gl/cogl-texture-driver-gl.c:274: GL error (1280): Invalid enumeration value


Cogl-WARNING **: ./driver/gl/cogl-texture-driver-gl.c:274: GL error (1280): Invalid enumeration value


Cogl-WARNING **: ./driver/gl/cogl-texture-driver-gl.c:274: GL error (1280): Invalid enumeration value


Cogl-WARNING **: ./driver/gl/cogl-texture-driver-gl.c:274: GL error (1280): Invalid enumeration value


Cogl-WARNING **: ./driver/gl/cogl-texture-driver-gl.c:274: GL error (1280): Invalid enumeration value


Cogl-WARNING **: ./driver/gl/cogl-texture-driver-gl.c:274: GL error (1280): Invalid enumeration value


Cogl-WARNING **: ./driver/gl/cogl-texture-driver-gl.c:274: GL error (1280): Invalid enumeration value


Cogl-WARNING **: ./driver/gl/cogl-texture-driver-gl.c:274: GL error (1280): Invalid enumeration value


Cogl-WARNING **: ./driver/gl/cogl-texture-driver-gl.c:274: GL error (1280): Invalid enumeration value


Cogl-WARNING **: ./driver/gl/cogl-texture-driver-gl.c:274: GL error (1280): Invalid enumeration value


Cogl-WARNING **: ./driver/gl/cogl-texture-driver-gl.c:274: GL error (1280): Invalid enumeration value


Cogl-WARNING **: ./driver/gl/cogl-texture-driver-gl.c:274: GL error (1280): Invalid enumeration value


Cogl-WARNING **: ./driver/gl/cogl-texture-driver-gl.c:274: GL error (1280): Invalid enumeration value


Cogl-WARNING **: ./driver/gl/cogl-texture-driver-gl.c:274: GL error (1280): Invalid enumeration value


Cogl-WARNING **: ./driver/gl/cogl-texture-driver-gl.c:274: GL error (1280): Invalid enumeration value


Cogl-WARNING **: ./driver/gl/cogl-texture-driver-gl.c:274: GL error (1280): Invalid enumeration value

Window manager warning: Log level 8: _shell_embedded_window_unrealize: assertion `SHELL_IS_EMBEDDED_WINDOW (window)' failed

Cogl-WARNING **: ./driver/gl/cogl-texture-driver-gl.c:274: GL error (1280): Invalid enumeration value


Cogl-WARNING **: ./driver/gl/cogl-texture-driver-gl.c:274: GL error (1280): Invalid enumeration value


Cogl-WARNING **: ./driver/gl/cogl-texture-driver-gl.c:274: GL error (1280): Invalid enumeration value


Cogl-WARNING **: ./driver/gl/cogl-texture-driver-gl.c:274: GL error (1280): Invalid enumeration value


Cogl-WARNING **: ./driver/gl/cogl-texture-driver-gl.c:274: GL error (1280): Invalid enumeration value


Cogl-WARNING **: ./driver/gl/cogl-texture-driver-gl.c:274: GL error (1280): Invalid enumeration value

Window manager warning: CurrentTime used to choose focus window; focus window may not be correct.
Window manager warning: CurrentTime used to choose focus window; focus window may not be correct.
Window manager warning: Got a request to focus the no_focus_window with a timestamp of 0.  This shouldn't happen!

Cogl-WARNING **: ./driver/gl/cogl-texture-driver-gl.c:274: GL error (1280): Invalid enumeration value


Cogl-WARNING **: ./driver/gl/cogl-texture-driver-gl.c:274: GL error (1280): Invalid enumeration value

09:21:17 AM: Indicators_Sound_Available() => 0
09:21:17 AM: Destroying the volume monitor object...
09:21:17 AM: >> ~guGIO_VolumeMonitor()
09:21:17 AM: << ~guGIO_VolumeMonitor()

LIBDBUSMENU-GLIB-WARNING **: Trying to remove a child that doesn't believe we're it's parent.

LIBDBUSMENU-GLIB-WARNING **: Trying to remove a child that doesn't believe we're it's parent.

LIBDBUSMENU-GLIB-WARNING **: Trying to remove a child that doesn't believe we're it's parent.

LIBDBUSMENU-GLIB-WARNING **: Trying to remove a child that doesn't believe we're it's parent.
Window manager warning: CurrentTime used to choose focus window; focus window may not be correct.
Window manager warning: CurrentTime used to choose focus window; focus window may not be correct.
Window manager warning: Got a request to focus the no_focus_window with a timestamp of 0.  This shouldn't happen!

GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed
gnome-session[674]: Gdk-WARNING: gnome-session: Fatal IO error 11 (Resource temporarily unavailable) on X server :0.


Gdk-WARNING **: gnome-settings-daemon: Fatal IO error 11 (Resource temporarily unavailable) on X server :0.

g_dbus_connection_real_closed: Remote peer vanished with error: Underlying GIOStream returned 0 bytes on an async read (g-io-error-quark, 0). Exiting.
XIO:  fatal IO error 11 (Resource temporarily unavailable) on X server ":0"
      after 21064 requests (21064 known processed) with 0 events remaining.

Gdk-WARNING **: gnome-terminal: Fatal IO error 104 (Connection reset by peer) on X server :0.


Gdk-WARNING **: nm-applet: Fatal IO error 11 (Resource temporarily unavailable) on X server :0.


Gdk-WARNING **: telepathy-indicator: Fatal IO error 11 (Resource temporarily unavailable) on X server :0.


Gdk-WARNING **: empathy: Fatal IO error 11 (Resource temporarily unavailable) on X server :0.

gnome-shell-google-calendar.py: Fatal IO error 11 (Resource temporarily unavailable) on X server :0.
ian baker ...
      <<<<THREAD>>>>   Getting events from Küchen-Team ...
      <<<<THREAD>>>>   Getting events from German Holidays ...
      <<<<THREAD>>>>   Getting events from Kossin works ...
      <<<<THREAD>>>>   #Updated events since March 2011 until March 2013
Checking if actual month events need update...
No need for update
Checking if actual month events need update...
No need for update
Checking if actual month events need update...
Scheduler starts updater thread...
      <<<<THREAD>>>>   Update months events around: March 2012 | months_back 12 | months_ahead 12
      <<<<THREAD>>>>   Getting events from brian baker ...
      <<<<THREAD>>>>   Getting events from Küchen-Team ...
      <<<<THREAD>>>>   Getting events from German Holidays ...
      <<<<THREAD>>>>   Getting events from Kossin works ...
      <<<<THREAD>>>>   #Updated events since March 2011 until March 2013
Checking if actual month events need update...
No need for update
Checking if actual month events need update...
No need for update
Checking if actual month events need update...
Scheduler starts updater thread...
      <<<<THREAD>>>>   Update months events around: March 2012 | months_back 12 | months_ahead 12
      <<<<THREAD>>>>   Getting events from brian baker ...
      <<<<THREAD>>>>   Getting events from Küchen-Team ...
      <<<<THREAD>>>>   Getting events from German Holidays ...
      <<<<THREAD>>>>   Getting events from Kossin works ...
      <<<<THREAD>>>>   #Updated events since March 2011 until March 2013
Checking if actual month events need update...
No need for update
Checking if actual month events need update...
No need for update
Checking if actual month events need update...
Scheduler starts updater thread...
      <<<<THREAD>>>>   Update months events around: March 2012 | months_back 12 | months_ahead 12
      <<<<THREAD>>>>   Getting events from brian baker ...
      <<<<THREAD>>>>   Getting events from Küchen-Team ...
      <<<<THREAD>>>>   Getting events from German Holidays ...
      <<<<THREAD>>>>   Getting events from Kossin works ...
      <<<<THREAD>>>>   #Updated events since March 2011 until March 2013
Checking if actual month events need update...
No need for update
Checking if actual month events need update...
No need for update
Checking if actual month events need update...
Scheduler starts updater thread...
      <<<<THREAD>>>>   Update months events around: March 2012 | months_back 12 | months_ahead 12
      <<<<THREAD>>>>   Getting events from brian baker ...
      <<<<THREAD>>>>   Getting events from Küchen-Team ...
      <<<<THREAD>>>>   Getting events from German Holidays ...
      <<<<THREAD>>>>   Getting events from Kossin works ...
      <<<<THREAD>>>>   #Updated events since March 2011 until March 2013

Gdk-WARNING **: gnome-screensaver: Fatal IO error 11 (Resource temporarily unavailable) on X server :0.

synapse: Fatal IO error 11 (Resource temporarily unavailable) on X server :0.
[32m[07:15:13.934187 GLib-GObject-Debug][0m Read-only property 'read-only-view' on class 'GeeReadOnlyList' has type 'GeeCollection' which is not equal to or more restrictive than the type 'GeeList' of the property on the interface 'GeeList'

[34m[07:15:13.942340 Info][0m [35m[HybridSearchPlugin][0m keeps in cache now 84 file names
[31m[07:15:15.245397 Gdk-Critical][0m IA__gdk_window_thaw_toplevel_updates_libgtk_only: assertion `private->update_and_descendants_freeze_count > 0' failed
g_dbus_connection_real_closed: Remote peer vanished with error: Underlying GIOStream returned 0 bytes on an async read (g-io-error-quark, 0). Exiting.

Received signal:15->'Terminated'
OK

g_dbus_connection_real_closed: Remote peer vanished with error: Underlying GIOStream returned 0 bytes on an async read (g-io-error-quark, 0). Exiting.

Received signal:15->'Terminated'

GLib-GIO-CRITICAL **: Error while sending AddMatch() message: The connection is closed

GLib-GIO-CRITICAL **: Error while sending AddMatch() message: The connection is closed

GLib-GIO-CRITICAL **: Error while sending AddMatch() message: The connection is closed

OK

xcb_connection_has_error() returned true
xcb_connection_has_error() returned true
WARNING: gnome-keyring:: couldn't send data: daemon closed connection
WARNING: gnome-keyring:: couldn't send data: daemon closed connection
xcb_connection_has_error() returned true
xcb_connection_has_error() returned true
WARNING: gnome-keyring:: couldn't send data: daemon closed connection
WARNING: gnome-keyring:: couldn't send data: daemon closed connection
xcb_connection_has_error() returned true
xcb_connection_has_error() returned true
WARNING: gnome-keyring:: couldn't send data: daemon closed connection
WARNING: gnome-keyring:: couldn't send data: daemon closed connection
xcb_connection_has_error() returned true
xcb_connection_has_error() returned true
WARNING: gnome-keyring:: couldn't send data: daemon closed connection
WARNING: gnome-keyring:: couldn't send data: daemon closed connection
xcb_connection_has_error() returned true
xcb_connection_has_error() returned true
WARNING: gnome-keyring:: couldn't send data: daemon closed connection
WARNING: gnome-keyring:: couldn't send data: daemon closed connection
xcb_connection_has_error() returned true
xcb_connection_has_error() returned true
WARNING: gnome-keyring:: couldn't send data: daemon closed connection
WARNING: gnome-keyring:: couldn't send data: daemon closed connection
xcb_connection_has_error() returned true
xcb_connection_has_error() returned true
WARNING: gnome-keyring:: couldn't send data: daemon closed connection
WARNING: gnome-keyring:: couldn't send data: daemon closed connection
xcb_connection_has_error() returned true
xcb_connection_has_error() returned true
WARNING: gnome-keyring:: couldn't send data: daemon closed connection
WARNING: gnome-keyring:: couldn't send data: daemon closed connection
xcb_connection_has_error() returned true
xcb_connection_has_error() returned true
WARNING: gnome-keyring:: couldn't send data: daemon closed connection
WARNING: gnome-keyring:: couldn't send data: daemon closed connection
xcb_connection_has_error() returned true
xcb_connection_has_error() returned true
WARNING: gnome-keyring:: couldn't send data: daemon closed connection
WARNING: gnome-keyring:: couldn't send data: daemon closed connection
xcb_connection_has_error() returned true
xcb_connection_has_error() returned true
WARNING: gnome-keyring:: couldn't send data: daemon closed connection
WARNING: gnome-keyring:: couldn't send data: daemon closed connection
xcb_connection_has_error() returned true
xcb_connection_has_error() returned true
WARNING: gnome-keyring:: couldn't send data: daemon closed connection
WARNING: gnome-keyring:: couldn't send data: daemon closed connection
xcb_connection_has_error() returned true
xcb_connection_has_error() returned true
WARNING: gnome-keyring:: couldn't send data: daemon closed connection
WARNING: gnome-keyring:: couldn't send data: daemon closed connection
xcb_connection_has_error() returned true
xcb_connection_has_error() returned true
WARNING: gnome-keyring:: couldn't send data: daemon closed connection
WARNING: gnome-keyring:: couldn't send data: daemon closed connection
xcb_connection_has_error() returned true
xcb_connection_has_error() returned true
WARNING: gnome-keyring:: couldn't send data: daemon closed connection
WARNING: gnome-keyring:: couldn't send data: daemon closed connection
xcb_connection_has_error() returned true
xcb_connection_has_error() returned true
WARNING: gnome-keyring:: couldn't send data: daemon closed connection
WARNING: gnome-keyring:: couldn't send data: daemon closed connection
xcb_connection_has_error() returned true
xcb_connection_has_error() returned true
WARNING: gnome-keyring:: couldn't send data: daemon closed connection
WARNING: gnome-keyring:: couldn't send data: daemon closed connection
xcb_connection_has_error() returned true
xcb_connection_has_error() returned true
mmap() failed: Cannot allocate memory
mmap() failed: Cannot allocate memory
mmap() failed: Cannot allocate memory
mmap() failed: Cannot allocate memory
mmap() failed: Cannot allocate memory
mmap() failed: Cannot allocate memory
mmap() failed: Cannot allocate memory
mmap() failed: Cannot allocate memory
mmap() failed: Cannot allocate memory
mmap() failed: Cannot allocate memory
mmap() failed: Cannot allocate memory
mmap() failed: Cannot allocate memory
mmap() failed: Cannot allocate memory
mmap() failed: Cannot allocate memory
mmap() failed: Cannot allocate memory
mmap() failed: Cannot allocate memory
mmap() failed: Cannot allocate memory
mmap() failed: Cannot allocate memory
mmap() failed: Cannot allocate memory
mmap() failed: Cannot allocate memory
mmap() failed: Cannot allocate memory
mmap() failed: Cannot allocate memory
mmap() failed: Cannot allocate memory
mmap() failed: Cannot allocate memory
mmap() failed: Cannot allocate memory
mmap() failed: Cannot allocate memory
mmap() failed: Cannot allocate memory
mmap() failed: Cannot allocate memory
mmap() failed: Cannot allocate memory
mmap() failed: Cannot allocate memory
WARNING: gnome-keyring:: couldn't send data: daemon closed connection
mmap() failed: Cannot allocate memory
mmap() failed: Cannot allocate memory
mmap() failed: Cannot allocate memory
mmap() failed: Cannot allocate memory
mmap() failed: Cannot allocate memory
mmap() failed: Cannot allocate memory
mmap() failed: Cannot allocate memory
mmap() failed: Cannot allocate memory
mmap() failed: Cannot allocate memory
mmap() failed: Cannot allocate memory
mmap() failed: Cannot allocate memory
mmap() failed: Cannot allocate memory
mmap() failed: Cannot allocate memory
mmap() failed: Cannot allocate memory
mmap() failed: Cannot allocate memory
mmap() failed: Cannot allocate memory
mmap() failed: Cannot allocate memory
mmap() failed: Cannot allocate memory
mmap() failed: Cannot allocate memory
mmap() failed: Cannot allocate memory
mmap() failed: Cannot allocate memory
mmap() failed: Cannot allocate memory
mmap() failed: Cannot allocate memory
mmap() failed: Cannot allocate memory
mmap() failed: Cannot allocate memory
mmap() failed: Cannot allocate memory
mmap() failed: Cannot allocate memory
mmap() failed: Cannot allocate memory
mmap() failed: Cannot allocate memory
mmap() failed: Cannot allocate memory
mmap() failed: Cannot allocate memory
mmap() failed: Cannot allocate memory
mmap() failed: Cannot allocate memory
mmap() failed: Cannot allocate memory
mmap() failed: Cannot allocate memory
mmap() failed: Cannot allocate memory
mmap() failed: Cannot allocate memory
mmap() failed: Cannot allocate memory
mmap() failed: Cannot allocate memory
mmap() failed: Cannot allocate memory
mmap() failed: Cannot allocate memory
mmap() failed: Cannot allocate memory
mmap() failed: Cannot allocate memory
mmap() failed: Cannot allocate memory
mmap() failed: Cannot allocate memory
mmap() failed: Cannot allocate memory
mmap() failed: Cannot allocate memory
mmap() failed: Cannot allocate memory
Window manager warning: Log level 16: gnome-shell: Fatal IO error 0 (Success) on X server :0.


** WARNING **: zeitgeist-datahub.vala:224: Unable to get name "org.gnome.zeitgeist.datahub" on the bus!

Gdk-WARNING **: XID collision, trouble ahead

Gdk-WARNING **: XID collision, trouble ahead

Gdk-WARNING **: XID collision, trouble ahead

GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed
third_party/tcmalloc/chromium/src/system-alloc.cc:423] SbrkSysAllocator failed.

GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed

print-notifications-plugin-CRITICAL **: gsd_print_notifications_plugin_finalize: assertion `plugin->priv != NULL' failed

GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed

GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed

Gdk-WARNING **: gnome-fallback-mount-helper: Fatal IO error 11 (Resource temporarily unavailable) on X server :0.


Gdk-WARNING **: bluetooth-applet: Fatal IO error 11 (Resource temporarily unavailable) on X server :0.

synapse: Fatal IO error 11 (Resource temporarily unavailable) on X server :0.
gnome-shell-google-calendar.py: Fatal IO error 11 (Resource temporarily unavailable) on X server :0.

Gdk-WARNING **: nm-applet: Fatal IO error 11 (Resource temporarily unavailable) on X server :0.

gtk-window-decorator: Fatal IO error 11 (Resource temporarily unavailable) on X server :0.0.
XIO:  fatal IO error 11 (Resource temporarily unavailable) on X server ":0"
      after 3210 requests (3210 known processed) with 0 events remaining.

Gdk-WARNING **: telepathy-indicator: Fatal IO error 11 (Resource temporarily unavailable) on X server :0.


Gdk-WARNING **: gnome-screensaver: Fatal IO error 11 (Resource temporarily unavailable) on X server :0.


GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed

Gdk-WARNING **: XID collision, trouble ahead

Gdk-WARNING **: XID collision, trouble ahead

Gdk-WARNING **: XID collision, trouble ahead
third_party/tcmalloc/chromium/src/system-alloc.cc:423] SbrkSysAllocator failed.

GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed
**
GLib-GIO:ERROR:/build/buildd/glib2.0-2.31.19+git20120229.c5b6f774/./gio/gdbusconnection.c:4678:call_in_idle_cb: assertion failed: (vtable != NULL && vtable->method_call != NULL)
** Message: PID 21338 (we are 5809) sent signal 15, shutting down...

Gdk-WARNING **: gnome-settings-daemon: Fatal IO error 11 (Resource temporarily unavailable) on X server :0.

x-session-manager[5721]: Gdk-WARNING: x-session-manager: Fatal IO error 11 (Resource temporarily unavailable) on X server :0.


Gdk-WARNING **: XID collision, trouble ahead

Gdk-WARNING **: XID collision, trouble ahead

Gdk-WARNING **: XID collision, trouble ahead

GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed
third_party/tcmalloc/chromium/src/system-alloc.cc:423] SbrkSysAllocator failed.

** CRITICAL **: nautilus_menu_provider_get_background_items: assertion `NAUTILUS_IS_MENU_PROVIDER (provider)' failed

** CRITICAL **: nautilus_menu_provider_get_background_items: assertion `NAUTILUS_IS_MENU_PROVIDER (provider)' failed

** CRITICAL **: nautilus_menu_provider_get_background_items: assertion `NAUTILUS_IS_MENU_PROVIDER (provider)' failed

** CRITICAL **: nautilus_menu_provider_get_background_items: assertion `NAUTILUS_IS_MENU_PROVIDER (provider)' failed

** CRITICAL **: nautilus_menu_provider_get_background_items: assertion `NAUTILUS_IS_MENU_PROVIDER (provider)' failed

** CRITICAL **: nautilus_menu_provider_get_background_items: assertion `NAUTILUS_IS_MENU_PROVIDER (provider)' failed

** CRITICAL **: nautilus_menu_provider_get_background_items: assertion `NAUTILUS_IS_MENU_PROVIDER (provider)' failed

** CRITICAL **: nautilus_menu_provider_get_background_items: assertion `NAUTILUS_IS_MENU_PROVIDER (provider)' failed

** CRITICAL **: nautilus_menu_provider_get_background_items: assertion `NAUTILUS_IS_MENU_PROVIDER (provider)' failed

** CRITICAL **: nautilus_menu_provider_get_background_items: assertion `NAUTILUS_IS_MENU_PROVIDER (provider)' failed

** CRITICAL **: nautilus_menu_provider_get_background_items: assertion `NAUTILUS_IS_MENU_PROVIDER (provider)' failed

** CRITICAL **: nautilus_menu_provider_get_file_items: assertion `NAUTILUS_IS_MENU_PROVIDER (provider)' failed

** CRITICAL **: nautilus_menu_item_list_free: assertion `item_list != NULL' failed

** CRITICAL **: nautilus_menu_item_list_free: assertion `item_list != NULL' failed

** CRITICAL **: nautilus_menu_item_list_free: assertion `item_list != NULL' failed

** CRITICAL **: nautilus_menu_provider_get_file_items: assertion `NAUTILUS_IS_MENU_PROVIDER (provider)' failed

** CRITICAL **: nautilus_menu_item_list_free: assertion `item_list != NULL' failed

** CRITICAL **: nautilus_menu_item_list_free: assertion `item_list != NULL' failed

** CRITICAL **: nautilus_menu_item_list_free: assertion `item_list != NULL' failed

** CRITICAL **: nautilus_menu_provider_get_file_items: assertion `NAUTILUS_IS_MENU_PROVIDER (provider)' failed

** CRITICAL **: nautilus_menu_item_list_free: assertion `item_list != NULL' failed

** CRITICAL **: nautilus_menu_item_list_free: assertion `item_list != NULL' failed

** CRITICAL **: nautilus_menu_item_list_free: assertion `item_list != NULL' failed

** CRITICAL **: nautilus_menu_provider_get_file_items: assertion `NAUTILUS_IS_MENU_PROVIDER (provider)' failed

** CRITICAL **: nautilus_menu_item_list_free: assertion `item_list != NULL' failed

** CRITICAL **: nautilus_menu_item_list_free: assertion `item_list != NULL' failed

** CRITICAL **: nautilus_menu_item_list_free: assertion `item_list != NULL' failed

** CRITICAL **: nautilus_menu_provider_get_file_items: assertion `NAUTILUS_IS_MENU_PROVIDER (provider)' failed

** CRITICAL **: nautilus_menu_item_list_free: assertion `item_list != NULL' failed

** CRITICAL **: nautilus_menu_item_list_free: assertion `item_list != NULL' failed

** CRITICAL **: nautilus_menu_item_list_free: assertion `item_list != NULL' failed

** CRITICAL **: nautilus_menu_provider_get_file_items: assertion `NAUTILUS_IS_MENU_PROVIDER (provider)' failed

** CRITICAL **: nautilus_menu_item_list_free: assertion `item_list != NULL' failed

** CRITICAL **: nautilus_menu_item_list_free: assertion `item_list != NULL' failed

** CRITICAL **: nautilus_menu_item_list_free: assertion `item_list != NULL' failed

** CRITICAL **: nautilus_menu_provider_get_file_items: assertion `NAUTILUS_IS_MENU_PROVIDER (provider)' failed

** CRITICAL **: nautilus_menu_item_list_free: assertion `item_list != NULL' failed

** CRITICAL **: nautilus_menu_item_list_free: assertion `item_list != NULL' failed

** CRITICAL **: nautilus_menu_item_list_free: assertion `item_list != NULL' failed

** CRITICAL **: nautilus_menu_provider_get_file_items: assertion `NAUTILUS_IS_MENU_PROVIDER (provider)' failed

** CRITICAL **: nautilus_menu_item_list_free: assertion `item_list != NULL' failed

** CRITICAL **: nautilus_menu_item_list_free: assertion `item_list != NULL' failed

** CRITICAL **: nautilus_menu_item_list_free: assertion `item_list != NULL' failed

** CRITICAL **: nautilus_menu_provider_get_file_items: assertion `NAUTILUS_IS_MENU_PROVIDER (provider)' failed

** CRITICAL **: nautilus_menu_item_list_free: assertion `item_list != NULL' failed

** CRITICAL **: nautilus_menu_provider_get_file_items: assertion `NAUTILUS_IS_MENU_PROVIDER (provider)' failed

** CRITICAL **: nautilus_menu_item_list_free: assertion `item_list != NULL' failed

** CRITICAL **: nautilus_menu_provider_get_file_items: assertion `NAUTILUS_IS_MENU_PROVIDER (provider)' failed

** CRITICAL **: nautilus_menu_provider_get_file_items: assertion `NAUTILUS_IS_MENU_PROVIDER (provider)' failed

** CRITICAL **: nautilus_menu_provider_get_file_items: assertion `NAUTILUS_IS_MENU_PROVIDER (provider)' failed

** CRITICAL **: nautilus_menu_provider_get_file_items: assertion `NAUTILUS_IS_MENU_PROVIDER (provider)' failed

** CRITICAL **: nautilus_menu_provider_get_file_items: assertion `NAUTILUS_IS_MENU_PROVIDER (provider)' failed

** CRITICAL **: nautilus_menu_item_list_free: assertion `item_list != NULL' failed

** CRITICAL **: nautilus_menu_provider_get_file_items: assertion `NAUTILUS_IS_MENU_PROVIDER (provider)' failed

** CRITICAL **: nautilus_menu_item_list_free: assertion `item_list != NULL' failed

** CRITICAL **: nautilus_menu_provider_get_file_items: assertion `NAUTILUS_IS_MENU_PROVIDER (provider)' failed

** CRITICAL **: nautilus_menu_item_list_free: assertion `item_list != NULL' failed

** CRITICAL **: nautilus_menu_provider_get_file_items: assertion `NAUTILUS_IS_MENU_PROVIDER (provider)' failed

** CRITICAL **: nautilus_menu_item_list_free: assertion `item_list != NULL' failed
```

---

### Post by Bobhuber on 2012-03-02
> **sgage said:**
> no ppa's here either, and neither gnome shell nor gnome fallback have any panels. It appears that nautilus is running - a right-click on the desktop brings up the appropriate context menu.
+1

---

### Post by bmbaker on 2012-03-02
> **tista said:**
> And now I've tried to run gnome-shell via "gnome-shell --replace" on terminal kicked in gnome-fallback session:

below is the fully log:
[http://paste.ubuntu.com/865195/]("http://paste.ubuntu.com/865195/")
I hope this could help the devs... ;)

P.S:
"gnome-shell --replace" could run gs normally... ??? what happened?
But anyway my gdm 3.2.1 also died... OMG... :(

hi tista :-)
How did you setup the ubuntu-paste?
cheers
BB

---

### Post by ricotz on 2012-03-02
> **tista said:**
> And now I've tried to run gnome-shell via &quot;gnome-shell --replace&quot; on terminal kicked in gnome-fallback session:

below is the fully log:
[http://paste.ubuntu.com/865195/](http://paste.ubuntu.com/865195/)
I hope this could help the devs... ;)


I hope you noticed that the versions you posted earlier are not completely visible. 
The warning in your log is known. But it should not crash instantly. 

Only try this if you know what is does/means: 
Using "gdb --args gnome-shell --replace --display :0 2>&1 | tee g-s.log" followed by "r" (run) and when it crashed "bt" (backtrace). Assuming you have the needed *-dbg packages installed (like gjs-dbg, mutter-dbg, gnome-shell-dbg, libclutter-1.0-0-dbg, libcogl8-dbg) 
Preferable this should be executed over ssh or on another tty since if g-s crashed your session will be frozen. g-s.log will contain the output.

---

### Post by tista on 2012-03-02
> **ricotz said:**
> I hope you noticed that the versions you posted earlier are not completely visible. 
The warning in your log is known. But it should not crash instantly. 

Only try this if you know what is does/means: 
Using "gdb --args gnome-shell --replace --display :0 2>&1 | tee g-s.log" followed by "r" (run) and when it crashed "bt" (backtrace). Assuming you have the needed *-dbg packages installed (like gjs-dbg, mutter-dbg, gnome-shell-dbg, libclutter-1.0-0-dbg, libcogl8-dbg) 
Preferable this should be executed over ssh or on another tty since if g-s crashed your session will be frozen. g-s.log will contain the output.

Hi Rico! ;)

Oh sorry for that...
Well here is the full version string of these packages:

```
ii  gnome-shell                                    3.3.90+git20120301.ff92d962-0ubuntu1~12.04~ricotz0   graphical shell for the GNOME desktop
ii  gjs                                            1.31.10+git20120301.83dd969e-0ubuntu1~12.04~ricotz0  Mozilla-based javascript bindings for the GNOME platform
ii  mutter                                         3.3.90+git20120301.860c2a62-0ubuntu1~12.04~ricotz0   lightweight GTK+ window manager

ii  libcogl7                                       1.9.5+git20120220.80ccf06b-0ubuntu1~12.04~ricotz0    Object oriented GL/GLES Abstraction/Utility Layer
ii  libcogl8                                       1.9.7+git20120224.60b8e988-0ubuntu1~12.04~ricotz0    Object oriented GL/GLES Abstraction/Utility Layer
ii  libclutter-1.0-0                               1.9.13+git20120301.018ede2b-0ubuntu1~12.04~ricotz1   Open GL based interactive canvas library
```

are those enough? ;)

and ASAP I would do gdb along with your suggestions...

cheers,
tista

---

### Post by Harry33 on 2012-03-02
The problem you all probably are having is due to the latest lightdm (1.1.4-0ubuntu1).
After that update you cannot start gnome-shell nor gnome-panel (classic session) either.

So, you have to downgrade to the older version of lightdm (1.1.3_0ubuntu1).
These packages must be downgraded:
- lightdm
- liblightdm-gobject-1-0

After the downgrade process, everything works again.
I have tried this on both my 64-bit and 32-bit installations.

I did the downgrade process from TTY1 (cntrl+alt+F1), then loggin in.
The wget [https://launchapd.net/](https://launchapd.net/)...
And after that:
sudo dpkg -i *.deb

The issue is there even if you had the no extra PPA's enabled.
I have two setups with pure Precise repos and one with Gnome3 PPA. The all got this issue.

---

### Post by ricotz on 2012-03-02
This is a good guide to get started for looking into debugging g-s problems. 

[https://live.gnome.org/GnomeShell/Debugging](https://live.gnome.org/GnomeShell/Debugging)

---

### Post by tista on 2012-03-02
> **ricotz said:**
> This is a good guide to get started for looking into debugging g-s problems. 

[https://live.gnome.org/GnomeShell/Debugging](https://live.gnome.org/GnomeShell/Debugging)

@rico

here is the output of gdb with your suggested command:
[http://paste.ubuntu.com/865309/]("http://paste.ubuntu.com/865309/")

Well gs didn't crash anytime while I'm debugging via gdb.. grrrrr


So if we have another bug on some other packages? ;)

Regards,
Tista

---

### Post by Harry33 on 2012-03-02
> **tista said:**
> @rico

here is the output of gdb with your suggested command:
[http://paste.ubuntu.com/865309/](http://paste.ubuntu.com/865309/)

Well gs didn't crash anytime while I'm debugging via gdb.. grrrrr


So if we have another bug on some other packages? ;)

Regards,
Tista

Try to downgrade lightdm.

---

### Post by tista on 2012-03-02
> **Harry33 said:**
> The problem you all probably are having is due to the latest lightdm (1.1.4-0ubuntu1).
After that update you cannot start gnome-shell nor gnome-panel (classic session) either.

So, you have to downgrade to the older version of lightdm (1.1.3_0ubuntu1).
These packages must be downgraded:
- lightdm
- liblightdm-gobject-1-0

After the downgrade process, everything works again.
I have tried this on both my 64-bit and 32-bit installations.

I did the downgrade process from TTY1 (cntrl+alt+F1), then loggin in.
The wget [https://launchapd.net/](https://launchapd.net/)...
And after that:
sudo dpkg -i *.deb

The issue is there even if you had the no extra PPA's enabled.
I have two setups with pure Precise repos and one with Gnome3 PPA. The all got this issue.

Hi harry33,

Unfortunately my gdm 3.2.1 also have this problem... :(
Too bad thing, gdm-greeter is now depending on the engine of gnome-shell you know.

So I didn't think this issue only caused the codes of lightdm.

Cheers,
Tista

**P.S:**
OMG! I made a mistake!!
You're right, once I purged all of lightdm packages and also even the unity-greeter, then I could login gnome-shell session via gdm...

That's miracle... are you esper?! ;)

...but still wrong gtk3 look&feel existed. :(

---

### Post by sgage on 2012-03-02
> **Harry33 said:**
> The problem you all probably are having is due to the latest lightdm (1.1.4-0ubuntu1).
After that update you cannot start gnome-shell nor gnome-panel (classic session) either.

So, you have to downgrade to the older version of lightdm (1.1.3_0ubuntu1).
These packages must be downgraded:
- lightdm
- liblightdm-gobject-1-0

After the downgrade process, everything works again.
I have tried this on both my 64-bit and 32-bit installations.

I did the downgrade process from TTY1 (cntrl+alt+F1), then loggin in.
The wget [https://launchapd.net/](https://launchapd.net/)...
And after that:
sudo dpkg -i *.deb

The issue is there even if you had the no extra PPA's enabled.
I have two setups with pure Precise repos and one with Gnome3 PPA. The all got this issue.

Thanks Harry! Downgrading to 1.1.3 worked for me...

---

### Post by bmbaker on 2012-03-02
ya thanks harry can confirm downgrading wked foir me too .-)
cheers

---

### Post by kurt18947 on 2012-03-02
I *knew* there was a reason to keep xfce-desktop installed :D.  This glitch killed my Unity, Unity2D, all variants of gnome-sesssion-fallback and gnome-shell. Xfce desktop is functioning correctly it seems.

---

### Post by bmbaker on 2012-03-02
funny unity and unity 2d was wking just not gnome and gnome-shell !!

---

### Post by kansasnoob on 2012-03-02
> **Harry33 said:**
> The problem you all probably are having is due to the latest lightdm (1.1.4-0ubuntu1).
After that update you cannot start gnome-shell nor gnome-panel (classic session) either.

So, you have to downgrade to the older version of lightdm (1.1.3_0ubuntu1).
These packages must be downgraded:
- lightdm
- liblightdm-gobject-1-0

After the downgrade process, everything works again.
I have tried this on both my 64-bit and 32-bit installations.

I did the downgrade process from TTY1 (cntrl+alt+F1), then loggin in.
The wget [https://launchapd.net/](https://launchapd.net/)...
And after that:
sudo dpkg -i *.deb

The issue is there even if you had the no extra PPA's enabled.
I have two setups with pure Precise repos and one with Gnome3 PPA. The all got this issue.

Super cool, that done it :)

Of course the smart thing to do is wait a day or two until it's fixed but I love to play, and I kill at least one install a day :D

---

### Post by 3togo on 2012-03-02
Do Consider using gdm instead of lightdm for the time being...

sudo apt-get install gdm

---

### Post by paul_in_london on 2012-03-02
> **3togo said:**
> Do Consider using gdm instead of lightdm for the time being...

sudo apt-get install gdm

Funnily enough I was playing around with **[COLOR="Red"]xdm[/COLOR]** earlier and it was failing to load the session (appeared to be trying to load unity, which is apparently referred to in "session-speak" as "ubuntu"). I don't have unity installed at all though.

Switching to **[COLOR="Red"]gdm[/COLOR]** for the time being solved the problem so maybe the **[COLOR="Red"]xdm[/COLOR]** problem I was having is related to this.

---

### Post by rburkartjo on 2012-03-02
xfce also working fine on my end

---

### Post by Harry33 on 2012-03-02
> **bmbaker said:**
> funny unity and unity 2d was wking just not gnome and gnome-shell !!

The newest lightdm tries to force start "session ubuntu", this is the reason it does not work with setups with gnome-shell only or with gnome-panel.
It seems it does not allow "session gnome" or "session classic".

---

### Post by magneze on 2012-03-02
Installing GDM worked for me. Thanks.

So, LightDM now only works with Unity? FFS :rolleyes:

---

### Post by zika on 2012-03-02
To circumvent problem You could also use .Xsession+startx...

---

### Post by keithpeter on 2012-03-02
> **3togo said:**
> Do Consider using gdm instead of lightdm for the time being...

sudo apt-get install gdm

Hello 3togo and all

Gnome Shell happy on nvidia card and restricted drivers with gdm, tap windows and search seems to be working fine where it crashes with LightDM.

All good fun

---

### Post by kurt18947 on 2012-03-02
> **keithpeter said:**
> Hello 3togo and all

Gnome Shell happy on nvidia card and restricted drivers with gdm, tap windows and search seems to be working fine where it crashes with LightDM.

All good fun

Agreed.  Install GDM, I restarted, select GDM as the default and all is well at least with gnome-shell

---

### Post by georgie on 2012-03-02
I had this same problem after upgrading to Precise.

Logging as me (with a profile that worked fine on 11.10/11.04) just left it hanging.

Switching to GDM instead of LightDM didn't help. 

Interestingly, 'Guest Session' loaded shell just fine.

I suspect some lingering shell extensions in my user profile are causing the problem. For now I'm happy in Classic or XFCE4.

---

### Post by Harry33 on 2012-03-02
There is a bug (944736) report in Launchpad about this now:
[https://bugs.launchpad.net/ubuntu/+source/lightdm/+bug/944736](https://bugs.launchpad.net/ubuntu/+source/lightdm/+bug/944736)

Also the version 1.1.4 of lightdm has now been reverted back to 1.1.3 by the newest update:
lightdm_4.1.1.is.1.1.3-0ubuntu1. This is soon in repos.

Here: 
[https://launchpad.net/ubuntu/precise/+source/lightdm/1.1.4.is.1.1.3-0ubuntu1](https://launchpad.net/ubuntu/precise/+source/lightdm/1.1.4.is.1.1.3-0ubuntu1)

Edit: Tried it and it works.

---

### Post by bmbaker on 2012-03-02
tried it too and the new update wks :-)

---

### Post by williammanda on 2012-03-02
Thanks for your help!

---

### Post by helicase on 2012-03-02
> **georgie said:**
> 
Interestingly, 'Guest Session' loaded shell just fine.

Same here. And after that my regular session suddenly worked, too.

---

