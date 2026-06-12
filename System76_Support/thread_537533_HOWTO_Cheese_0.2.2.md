---
title: "HOWTO: Cheese 0.2.2"
date: 2007-08-29
forum: System76 Support
---

### Post by poetbeware on 2007-08-29
So in another thread, a poster pointed out that the daru2's camera worked with a program called "Cheese", but only the latest version. 

Cheese is a nifty utility that lets you take a picture using the darter's built-in camera. It's really useful for me when I'm doing animation work, because I can quickly get a reference photo for a facial expression.

Here's what I did to install Cheese 0.2.2, may you have an easier time doing all this than I did:

1. Install all the dependencies. In a terminal:

```

apt-get install libglib2.0-dev libgtk2.0-dev libglade2-dev libdbus-1-dev libgstreamer0.10-dev libgstreamer-plugins-base0.10-dev libgnomevfs2-dev libgnomeui-dev libebook1.2-dev gettext

```

2. Download the source code from [here]("http://live.gnome.org/Cheese/Releases?action=AttachFile&do=get&target=cheese-0.2.2.tar.gz"). 

3. In a terminal:

```

tar -xzf cheese-0.2.2.tar.gz
cd cheese-0.2.2.tar.gz
./configure
make
sudo make install

```

4. You should now have a menu item under Applications/Accessories/Cheese.

5. It might not work until you configure gstreamer. In a terminal:

```

gstreamer-properties

```

Under the "video" tab, select "Autodetect" for Default Output plugin and "Video for Linux 2 (v4l2)" for Default Input plugin.

Hope that helps...

---

### Post by thomasaaron on 2007-08-29
Nice how-to.
Thank you for that contribution.

---

### Post by palintheus on 2007-08-29
There is also a .deb that will do this for you, for those that are opposed to CLI. Just search for it at getdeb.net

---

