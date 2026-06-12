---
title: "Bittorrent clients for the future!"
date: 2008-01-02
forum: The Cafe
---

### Post by Centx on 2008-01-02
With Bittorrent being as popular as it is, it's inevitable that new clients spring to life now and then, and I for one would like to know what alternatives (new ones that is) there is.

I have found some that I believe have some real potential (I shurely have missed someone though:KS).

And here they are, in random order, plus a little of what their "owners" have to say about them:

[**bitswash**]("http://www.bitswash.org/") - wxwidgets
"Bitswash is a bittorrent client built on crossplatform library wxWidgets, libtorrent and boost library. It supports multiple torrent downloading, automatic queue management, protocol encryption, peer exchange, upnp, natpmp, lsd, and IP and file filtering. "[www.bitswash.org]("http://www.bitswash.org/") 

[**linkage**]("http://code.google.com/p/linkage/") - GTK
"Linkage is a BitTorrent client written in C++ using gtkmm and libtorrent.
Linkage is a lightweight client, it includes most common features found in other BitTorrent clients. And also some unique feature..."[code.google.com/p/linkage/]("http://code.google.com/p/linkage/")

[**qbittorrent**]("http://qbittorrent.sourceforge.net/") - QT4
"The qBittorrent project was created in March 2006 with the idea of developping a new Bittorrent client for Linux (and possibly other systems) that would be easy to use, good looking, featureful but lightweight."[qbittorrent.sourceforge.net]("http://qbittorrent.sourceforge.net/")

[**torrentflux-b4rt**]("http://tf-b4rt.berlios.de/") - Web
"Torrentflux-b4rt was originally based on the TorrentFlux BitTorrent controller written by Qrome, although has recently undergone a major rewrite to allow transparent integration with a number of transfer clients and protocols."[tf-b4rt.berlios.de]("http://tf-b4rt.berlios.de/")

[**btg**]("http://developer.berlios.de/projects/btg/") - GUI(gktmm), CLI and web
"Linux bittorrent client implemented in C++ and using the libtorrent library. Provides both ncurses and gtkmm gui, which communicate with a common backend running the actual bittorrent operation."[developer.berlios.de/projects/btg/]("http://developer.berlios.de/projects/btg/")



So, what do you think? do you see any of these as major clients in the years to come?

---

### Post by Sockerdrickan on 2008-01-02
I think Transmission will continue to gain market share :P

---

### Post by rabid9797 on 2008-01-02
> **Tux0r said:**
> I think Transmission will continue to gain market share :P

this man speaks the truth

---

### Post by dannyboy79 on 2008-01-02
well, most private trackers won't just let you use ANY client. With that said, I use Bittornado in linux as well as windows. The only thing I haven't figured out yet is how do I get it to shut down after it seeds back 100%.

---

### Post by Enginirical on 2008-01-02
I've been using qBittorrent, people seem to keep ignoring it, but it's AWESOME, best client used so far. 

It&#347; not overcomplicated, it just works, and it&#347; fast and doesnt infringe on performance of other applications. It has directory scanning with automated download of torrents inside so no manual jumping around torrent sites. It has 5 major search engines pre-installed with loads of plugins available to expand this. (yes it's Qt4, but so what? isn't that the most ridiculous reason not to choose a client, it works this well? It looks good enough if you a clever with your colour settings)

Definitely worth checking out, here is a blog that compares it against other torrent clients:

[http://tuxoblog.blogspot.com/search/label/Reviews](http://tuxoblog.blogspot.com/search/label/Reviews)

---

### Post by bobbocanfly on 2008-01-02
> **dannyboy79 said:**
> well, most private trackers won't just let you use ANY client. With that said, I use Bittornado in linux as well as windows. The only thing I haven't figured out yet is how do I get it to shut down after it seeds back 100%.

A lot of the private trackers i am on only allow uTorrent 1.7.5 which thankfully works in Wine.

---

### Post by Mateo on 2008-01-02
Linkage sounds interesting, but i'm going through a frustrating case of dependency-hell trying to get it to install.  I've installed at least 20 packages, mostly -devs, and it's still not working.  i installed about 10 for Linkage, but then had to install libtorrent from source as well (because the repo version is not new enough), and have been going through dependency-hell with it too.

I can handle errors during ./configure, but errors during make are almost impossible to figure out for non-programmers.

---

### Post by lunke on 2008-01-02
4 of the listed clients are essentially the same (linkage, qbittorrent, bitswash, btg and as well as deluge), at least they use the same backend, namely [http://libtorrent.org](http://libtorrent.org) :)

Transmission is a great lightweight alternative.

@Mateo: mail the errors you get while building to linkage's google group and I'll try to help you out. Other than that comments/suggestions are always welcome.

I primarily use Fedora so help with building .debs for linkage would be appriciated ;)

---

### Post by zolero on 2008-01-27
I've had the same problems with building Linkage from source on Gutsy and these were the problems encountered even when i've tryed out the SVN-way.
Afther these tryed out a litle dirty workaround: using other distros' RPMs converted to deb. Bad luck... :sad: but i've found that Fedora packages were built against libboost-date-time.so.2 and company...
OK. What now? I've grabbed some Boost RPMs providing that, converted and installed them. Another problem: this is vers. 1.33.1; thus need to downgrade from Gutsy's 1.34.1 grrr... But some other Gutsy's packages depends on this version, thus i need them. Bad luck again... dependencies and conflicts!  :mad:  
This issue was solved by rebuilding debs obtained from alien conversion to installing themselves in /usr/local and changed packages name to libboost-old to avoid conflicts. Well done... now version conflicts were figured out. :)=D>  ( If anyone need them just ask for ;) ) Don't worry: other problems coming...
From this point i was able to compile Linkage, but when i tryed out the package client won't start at all! Very weird... it seems to be something with GTK an DBus, but i can't figure out them. Below i post the terminal outputs with the error messages which i've got. Please help. Thanks in advance for yor kindness.

Configure command used to build linkage-0.1.4

```
root@asustopi:~/linkage-0.1.4-4.fc8.src/linkage-0.1.4# ./configure --prefix=/usr --enable-static=yes --with-curl=yes --with-gupnp=yes --with-gnome=yes --with-gnu-ld=yes --with-pic=yes --with-dbus-cpp=yes --with-upnp=yes --with-ssl=yes --with-notify-gtk2=yes --with-rb-libtorrent=yes --without-exo

```

First build attempts' compiling errors (figured out from now):

```
root@asustopi:~/linkage-0.1.4-4.fc8.src/linkage-0.1.4# make
...
...
...

libgdk_pixbuf-2.0.so /usr/lib/libpangocairo-1.0.so -lXext -lXinerama -lXi -lXrandr -lXcursor -lXcomposite -lXdamage /usr/lib/libpango-1.0.so /usr/lib/libcairo.so /usr/lib/libfreetype.so -lz -lfontconfig -lpng12 -lXrender -lX11 -lXfixes -ltorrent -ldbus-glib-1 -ldbus-1 -lgconfmm-2.6 /usr/lib/libglibmm-2.4.so /usr/lib/libgconf-2.so /usr/lib/libsigc-2.0.so /usr/lib/libORBit-2.so /usr/lib/libgmodule-2.0.so -ldl /usr/lib/libgthread-2.0.so -lrt /usr/lib/libgobject-2.0.so /usr/lib/libglib-2.0.so 
/usr/bin/ld: warning: libboost_date_time.so.2, needed by /usr/lib/libtorrent.so, not found (try using -rpath or -rpath-link)
/usr/bin/ld: warning: libboost_filesystem.so.2, needed by /usr/lib/libtorrent.so, not found (try using -rpath or -rpath-link)
/usr/bin/ld: warning: libboost_thread.so.2, needed by /usr/lib/libtorrent.so, not found (try using -rpath or -rpath-link)
TorrentCreator.o: In function `TorrentCreator::add_files(libtorrent::torrent_info&, Glib::ustring const&, Glib::ustring const&)':
/linkage-0.1.4-4.fc8.src/linkage-0.1.4/src/TorrentCreator.cc:218: undefined reference to `libtorrent::torrent_info::add_file(boost::filesystem::basic_path<std::basic_string<char, std::char_traits<char>, std::allocator<char> >, boost::filesystem::path_traits>, long long)'
TorrentCreator.o: In function `file_pool':
/usr/include/libtorrent/file_pool.hpp:67: undefined reference to `boost::mutex::mutex()'
TorrentCreator.o: In function `TorrentCreator::on_button_save()':
/linkage-0.1.4-4.fc8.src/linkage-0.1.4/src/TorrentCreator.cc:156: undefined reference to `libtorrent::storage::storage(libtorrent::torrent_info const&, boost::filesystem::basic_path<std::basic_string<char, std::char_traits<char>, std::allocator<char> >, boost::filesystem::path_traits> const&, libtorrent::file_pool&)'
TorrentCreator.o: In function `~file_pool':
/usr/include/libtorrent/file_pool.hpp:66: undefined reference to `boost::mutex::~mutex()'
/usr/include/libtorrent/file_pool.hpp:66: undefined reference to `boost::mutex::~mutex()'
UI.o: In function `boost::date_time::month_formatter<boost::gregorian::greg_month, boost::date_time::simple_format<char>, char>::format_month(boost::gregorian::greg_month const&, std::basic_ostream<char, std::char_traits<char> >&)':
/usr/include/boost/date_time/date_formatting.hpp:44: undefined reference to `boost::gregorian::greg_month::as_short_string() const'
/usr/lib/libtorrent.so: undefined reference to `boost::filesystem::path::is_complete() const'
/usr/lib/libtorrent.so: undefined reference to `boost::filesystem::no_check(std::basic_string<char, std::char_traits<char>, std::allocator<char> > const&)'
/usr/lib/libtorrent.so: undefined reference to `boost::filesystem::create_directory(boost::filesystem::path const&)'
/usr/lib/libtorrent.so: undefined reference to `boost::detail::condition_impl::condition_impl()'
/usr/lib/libtorrent.so: undefined reference to `boost::thread::thread(boost::function0<void, std::allocator<boost::function_base> > const&)'
/linkage-0.1.4-4.fc8.src/linkage-0.1.4/lib/.libs/liblinkage-1.so: undefined reference to `libtorrent::torrent_handle::move_storage(boost::filesystem::basic_path<std::basic_string<char, std::char_traits<char>, std::allocator<char> >, boost::filesystem::path_traits> const&) const'
/usr/lib/libtorrent.so: undefined reference to `boost::filesystem::path::path(char const*)'
/usr/lib/libtorrent.so: undefined reference to `boost::filesystem::path::operator<(boost::filesystem::path const&) const'
/usr/lib/libtorrent.so: undefined reference to `boost::filesystem::path::path(std::basic_string<char, std::char_traits<char>, std::allocator<char> > const&)'
/usr/lib/libtorrent.so: undefined reference to `boost::filesystem::rename(boost::filesystem::path const&, boost::filesystem::path const&)'
/usr/lib/libtorrent.so: undefined reference to `boost::filesystem::path::default_name_check(bool (*)(std::basic_string<char, std::char_traits<char>, std::allocator<char> > const&))'
/usr/lib/libtorrent.so: undefined reference to `boost::filesystem::complete(boost::filesystem::path const&, boost::filesystem::path const&)'
/usr/lib/libtorrent.so: undefined reference to `boost::detail::condition_impl::do_wait(pthread_mutex_t*)'
/linkage-0.1.4-4.fc8.src/linkage-0.1.4/lib/.libs/liblinkage-1.so: undefined reference to `libtorrent::session::add_torrent(libtorrent::torrent_info const&, boost::filesystem::basic_path<std::basic_string<char, std::char_traits<char>, std::allocator<char> >, boost::filesystem::path_traits> const&, libtorrent::entry const&, bool, int)'
/usr/lib/libtorrent.so: undefined reference to `boost::thread::join()'
/usr/lib/libtorrent.so: undefined reference to `boost::filesystem::file_size(boost::filesystem::path const&)'
/usr/lib/libtorrent.so: undefined reference to `boost::thread::~thread()'
/usr/lib/libtorrent.so: undefined reference to `boost::mutex::do_unlock()'
/usr/lib/libtorrent.so: undefined reference to `boost::filesystem::path::iterator::increment()'
/usr/lib/libtorrent.so: undefined reference to `boost::filesystem::path::begin() const'
/usr/lib/libtorrent.so: undefined reference to `boost::mutex::do_lock()'
/usr/lib/libtorrent.so: undefined reference to `boost::filesystem::path::has_branch_path() const'
/usr/lib/libtorrent.so: undefined reference to `boost::filesystem::path::branch_path() const'
/usr/lib/libtorrent.so: undefined reference to `boost::lock_error::~lock_error()'
/usr/lib/libtorrent.so: undefined reference to `boost::recursive_mutex::do_unlock()'
/usr/lib/libtorrent.so: undefined reference to `boost::filesystem::path::default_name_check_writable()'
/usr/lib/libtorrent.so: undefined reference to `boost::filesystem::create_directories(boost::filesystem::path const&)'
/usr/lib/libtorrent.so: undefined reference to `typeinfo for boost::lock_error'
/usr/lib/libtorrent.so: undefined reference to `boost::filesystem::is_directory(boost::filesystem::path const&)'
/usr/lib/libtorrent.so: undefined reference to `boost::recursive_mutex::recursive_mutex()'
/usr/lib/libtorrent.so: undefined reference to `boost::filesystem::last_write_time(boost::filesystem::path const&)'
/usr/lib/libtorrent.so: undefined reference to `boost::mutex::do_unlock(boost::mutex::cv_state&)'
/usr/lib/libtorrent.so: undefined reference to `boost::filesystem::path::native_file_string() const'
/usr/lib/libtorrent.so: undefined reference to `boost::mutex::do_lock(boost::mutex::cv_state&)'
/usr/lib/libtorrent.so: undefined reference to `boost::recursive_mutex::~recursive_mutex()'
/usr/lib/libtorrent.so: undefined reference to `boost::filesystem::initial_path()'
/usr/lib/libtorrent.so: undefined reference to `boost::detail::condition_impl::notify_all()'
/usr/lib/libtorrent.so: undefined reference to `boost::detail::condition_impl::notify_one()'
/usr/lib/libtorrent.so: undefined reference to `boost::lock_error::lock_error()'
/usr/lib/libtorrent.so: undefined reference to `boost::filesystem::path::operator/=(boost::filesystem::path const&)'
/usr/lib/libtorrent.so: undefined reference to `boost::detail::condition_impl::~condition_impl()'
/usr/lib/libtorrent.so: undefined reference to `boost::recursive_mutex::do_lock()'
/usr/lib/libtorrent.so: undefined reference to `boost::filesystem::exists(boost::filesystem::path const&)'
collect2: ld returned 1 exit status
make[2]: *** [linkage] Error 1
make[2]: Leaving directory `/linkage-0.1.4-4.fc8.src/linkage-0.1.4/src'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/linkage-0.1.4-4.fc8.src/linkage-0.1.4'
make: *** [all] Error 2
root@asustopi:~/linkage-0.1.4-4.fc8.src/linkage-0.1.4#
```

Now the errors when trying launch in terminal:

```
root@asustopi:~/Worker/Linkage# linkage

(linkage:17273): GnomeUI-WARNING **: While connecting to session manager:
Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed.

** (linkage:17273): WARNING **: Failed to connect to the D-BUS daemon: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.
process 17273: arguments to dbus_connection_get_data() were incorrect, assertion "connection != NULL" failed in file dbus-connection.c line 5551.
This is normally a bug in some application using the D-Bus library.
process 17273: arguments to dbus_connection_set_data() were incorrect, assertion "connection != NULL" failed in file dbus-connection.c line 5515.
This is normally a bug in some application using the D-Bus library.

** ERROR **: Not enough memory to set up DBusConnection for use with GLib
aborting...
root@asustopi:~/Worker/Linkage# 
```

The second error screen:

```
root@asustopi:~/Worker/Linkage# linkage

(linkage:17623): GnomeUI-WARNING **: While connecting to session manager:
Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed.

** (linkage:17623): WARNING **: Failed to connect to the D-BUS daemon: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.
process 17623: arguments to dbus_connection_get_data() were incorrect, assertion "connection != NULL" failed in file dbus-connection.c line 5551.
This is normally a bug in some application using the D-Bus library.
process 17623: arguments to dbus_connection_set_data() were incorrect, assertion "connection != NULL" failed in file dbus-connection.c line 5515.
This is normally a bug in some application using the D-Bus library.

** ERROR **: Not enough memory to set up DBusConnection for use with GLib
aborting...
root@asustopi:~/Worker/Linkage# 
```

And finally the third one:

```
root@asustopi:~# linkage

(linkage:5683): Gtk-CRITICAL **: gtk_window_resize: assertion `width > 0' failed
terminate called after throwing an instance of 'Glib::FileError'
aborting...
shooter@asustopi:~# 

```


_**Edit:**_ Excuse my bad english. I'm not english native... If this is an off please admins to move it to the right place. I haven't offing intention. Thanks.

---

### Post by Quillz on 2008-01-27
The thing is, as many clients as there are, we already have "winners" of sort. On Windows, the best is uTorrent. On the Mac, Transmission is becoming the strongest client. And on Linux, we have Azureus and Transmission.

---

### Post by Polygon on 2008-01-27
dont forget deluge, deluge is becoming highly popular, especially on linux. It also has mac and windows ports.

---

### Post by ~LoKe on 2008-01-27
rTorrent.  I don't understand the need for such a complex GUI which will just cause someone to screw something up.

---

### Post by koleoptero on 2008-01-27
I use deluge and I think it's the best choice at the moment. Transmission also worked perfectly but I couldn't get it to stop seeding after reaching a certain ratio.

---

### Post by hhhhhx on 2008-01-27
all i want is a *native* utorrent, no other that i have found beats it.  sorry but ktorrent or deluge just don't cut it.  :(

---

### Post by inversekinetix on 2008-01-27
uTorrent 1.6.1  is by far the best client I have used.  fast, feature packed, highly customizable.

---

### Post by ynnhoj on 2008-01-27
> **~LoKe said:**
> rTorrent.  I don't understand the need for such a complex GUI which will just cause someone to screw something up.
i'll say!  rtorrent does all i need it to and it's nice and simple.

---

### Post by bruce89 on 2008-01-27
> **Tux0r said:**
> I think Transmission will continue to gain market share :P

Due to this:

```

ubuntu-meta (1.87) hardy; urgency=low

  * Refreshed dependencies
[...]
  * Added transmission-gtk to desktop-recommends-i386, desktop-
    recommends-amd64, desktop-recommends-powerpc, desktop-recommends-
    ia64, desktop-recommends-sparc, desktop-recommends-hppa, desktop-
    recommends-lpia
[...]
  * Removed gnome-btdownload from desktop-i386, desktop-amd64, desktop-
    powerpc, desktop-ia64, desktop-sparc, desktop-hppa, desktop-lpia
[...]

 -- Martin Pitt <martin.pitt@ubuntu.com>  Mon, 14 Jan 2008 18:30:14 +0100

```

---

### Post by Polygon on 2008-01-28
finally. took them long enough to get rid of that crappy gnome torrent download program, which was really bad for trackers as once it finished, you closed it and you never seeded back what you dled.

---

### Post by bufsabre666 on 2008-01-28
> **xhhux said:**
> all i want is a *native* utorrent, no other that i have found beats it.  sorry but ktorrent or deluge just don't cut it.  :(

utorrent ia by far the best i ever used but im big fan of deluge and azureus, i wouldnt say they dont cut it, i just like utorrents very simple GUI

but as long as we're on linux ill stay with deluge until it gives me problems then i goto azureus ((although since i upgraded deluge it works just fine again))

---

### Post by graabein on 2008-01-28
**uTorrent** and **foobar2000** are the only programs I miss from Windows (OK maybe **Photoshop** and **Visual Studio** also). I used to have **Azureus** on Ubuntu but it was such a hog on my dated hardware so I've recently switched to **Deluge** and I think it's great. 

I don't know about the seeding stuff on **Deluge**... I'd like to use labels and seed certain torrents because of stupid ratio regulations where I get ballgames.

---

### Post by Polygon on 2008-01-28
i tried transmission, and had to compile it myself as the getdeb deb didnt work (couldent choose where to save a file), and after i added a torrent, it wouldent connect to any peers. I tried the same torrent in deluge and got like 10 seeders and 4 peers and was downloading at 100 kb/s

oh well.

---

### Post by ezphilosophy on 2008-01-28
I have been using ktorrent for quite some time.  I haven't found anything it can't do.  I tried deluge based on others advice, but I think in no way it stacks up to ktorrent. 

It might be interesting to see a table of different torrent clients and show a comparison to what they can and cannot do.  Does something like this already exist?

qbittorrent does look nice.  I will give it a try.  Thanks Centx for info.

---

### Post by bufsabre666 on 2008-01-28
> **ezphilosophy said:**
> 
It might be interesting to see a table of different torrent clients and show a comparison to what they can and cannot do.  Does something like this already exist?

[http://en.wikipedia.org/wiki/BitTorrent_client](http://en.wikipedia.org/wiki/BitTorrent_client)

:popcorn:

---

### Post by ezphilosophy on 2008-01-28
Thanks bufsabre66.  I guess I was talking about a table with even more comparisons.  For example, ktorrent has an option to move completed downloads to another folder.  So, I have a folder named "unfinished" and another named "finished".  Just a little more organized.  :)    Nevertheless, that table does a pretty good job. (although I live in China and have to use answers.com)        [http://www.answers.com/BitTorrent_client](http://www.answers.com/BitTorrent_client)

---

### Post by Sockerdrickan on 2008-01-28
> **bruce89 said:**
> Due to this:

```

ubuntu-meta (1.87) hardy; urgency=low

  * Refreshed dependencies
[...]
  * Added transmission-gtk to desktop-recommends-i386, desktop-
    recommends-amd64, desktop-recommends-powerpc, desktop-recommends-
    ia64, desktop-recommends-sparc, desktop-recommends-hppa, desktop-
    recommends-lpia
[...]
  * Removed gnome-btdownload from desktop-i386, desktop-amd64, desktop-
    powerpc, desktop-ia64, desktop-sparc, desktop-hppa, desktop-lpia
[...]

 -- Martin Pitt <martin.pitt@ubuntu.com>  Mon, 14 Jan 2008 18:30:14 +0100

```

I saw this too in a daily build yay :lolflag:

---

### Post by bufsabre666 on 2008-01-28
maybe its just me but transmission has the ugliest gui ever

i think they should of gone with deluge, but then again my favorte tracker recently blocked alot of clients and deluge is one the list

---

### Post by zekopeko on 2008-01-28
> **ezphilosophy said:**
> Thanks bufsabre66.  I guess I was talking about a table with even more comparisons.  For example, ktorrent has an option to move completed downloads to another folder.  So, I have a folder named "unfinished" and another named "finished".  Just a little more organized.  :)    Nevertheless, that table does a pretty good job. (although I live in China and have to use answers.com)        [http://www.answers.com/BitTorrent_client](http://www.answers.com/BitTorrent_client)

deluge those that. with a plugin that's part of the base system. the next version (0.6) is going to have a backend + frontend design meaning: a whole lot of GUI's for it ie. gnome gui, kde gui , CLI gui , webgui etc.

---

