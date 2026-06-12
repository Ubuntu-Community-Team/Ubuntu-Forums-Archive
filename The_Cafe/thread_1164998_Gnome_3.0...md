---
title: "Gnome 3.0.."
date: 2009-05-20
forum: The Cafe
---

### Post by nolliecrooked on 2009-05-20
is there a repo you can add to Jaunty to test it?

---

### Post by SunnyRabbiera on 2009-05-20
> **nolliecrooked said:**
> is there a repo you can add to Jaunty to test it?

I dont even think its in the alpha stages yet

---

### Post by Regenweald on 2009-05-20
Building it is actually quite easy. Just check the Gnome Live! page. You can do it in about three steps.

[http://live.gnome.org/GnomeShell#building](http://live.gnome.org/GnomeShell#building)

---

### Post by nolliecrooked on 2009-05-20
> **Regenweald said:**
> Building it is actually quite easy. Just check the Gnome Live! page. You can do it in about three steps.

[http://live.gnome.org/GnomeShell#building](http://live.gnome.org/GnomeShell#building)

yeah, its not working, it craps out with;

kieran@kieran-desktop:~$ curl -O [http://git.gnome.org/cgit/gnome-shell/plain/tools/build/gnome-shell-build-setup.sh](http://git.gnome.org/cgit/gnome-shell/plain/tools/build/gnome-shell-build-setup.sh)

  % Total    % Received % Xferd  Average Speed   Time    Time     Time  Current
                                 Dload  Upload   Total   Spent    Left  Speed
100  5619  100  5619    0     0   7590      0 --:--:-- --:--:-- --:--:-- 20513
kieran@kieran-desktop:~$ /bin/bash gnome-shell-build-setup.sh
Checking out jhbuild into /home/kieran/Source/jhbuild ... gnome-shell-build-setup.sh: line 162: git: command not found
kieran@kieran-desktop:~$

I did the sudo apt-get install git, but that didnt help ](*,)

---

### Post by Simian Man on 2009-05-20
Looks like you need to install git.

---

### Post by nolliecrooked on 2009-05-20
> **Simian Man said:**
> Looks like you need to install git.

read my post again :P

---

### Post by ashmew2 on 2009-05-20
As far as i know , you should be able to install it from Gutsy Backports using Prevu : [https://wiki.ubuntu.com/Prevu](https://wiki.ubuntu.com/Prevu)

---

### Post by GrouchoMarx on 2009-05-20
make sure to also install git-core

---

### Post by Simian Man on 2009-05-20
> **nolliecrooked said:**
> read my post again :P

Ah sorry :).  So if you type 'which git' at the terminal what does it tell you?

---

### Post by nolliecrooked on 2009-05-20
> **GrouchoMarx said:**
> make sure to also install git-core

+1. it worksssssssssss. thanks man (y)

---

### Post by nolliecrooked on 2009-05-20
ok, now it craps out with;

*** Checking out gobject-introspection *** [1/6]
git pull --rebase
Current branch master is up to date.
*** Configuring gobject-introspection *** [1/6]
./autogen.sh --prefix /home/kieran/gnome-shell/install --libdir '/home/kieran/gnome-shell/install/lib'  --disable-static --disable-gtk-doc 
You need to install the gnome-common module and make
sure the gnome-autogen.sh script is in your $PATH.
*** error during phase configure of gobject-introspection: ########## Error running ./autogen.sh --prefix /home/kieran/gnome-shell/install --libdir '/home/kieran/gnome-shell/install/lib'  --disable-static --disable-gtk-doc  *** [1/6]

  [1] rerun phase configure
  [2] ignore error and continue to build
  [3] give up on module
  [4] start shell
  [5] reload configuration
  [6] go to phase force_checkout
  [7] go to phase clean
  [8] go to phase distclean
choice: 

whats gnome-common module?

---

### Post by GrouchoMarx on 2009-05-20
Try deleting the gnome-shell directory and pulling it from scratch. When I tried it, the build phase was still flakey, and only worked after several attempts.

---

### Post by nolliecrooked on 2009-05-20
> **GrouchoMarx said:**
> Try deleting the gnome-shell directory and pulling it from scratch. When I tried it, the build phase was still flakey, and only worked after several attempts.

I did, now it says...

No package 'gobject-2.0' found
No package 'gio-2.0' found

Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix.

Alternatively, you may set the environment variables GOBJECT_CFLAGS
and GOBJECT_LIBS to avoid the need to call pkg-config.
See the pkg-config man page for more details.

---

### Post by GrouchoMarx on 2009-05-20
You can try the following, which rebuilds everything from scratch:

> jhbuild build -f -a -c

---

### Post by nolliecrooked on 2009-05-20
> **GrouchoMarx said:**
> You can try the following, which rebuilds everything from scratch:

ugh, same problem.

forget it im not that curious ](*,)](*,)](*,)

---

### Post by ashmew2 on 2009-05-20
Dont give up that easily man ;)

---

### Post by Xyhthyx on 2009-05-20
Why is everyone calling Gnome Shell "Gnome 3"?

---

### Post by RiceMonster on 2009-05-20
> **Xyhthyx said:**
> Why is everyone calling Gnome Shell "Gnome 3"?

Because the last version was 2?

---

### Post by celticbhoy on 2009-05-21
I keep getting this 

> WARNING: Skipping unknown interface GtkFileChooserEmbed
warning: Interface 'Activatable' virtual function 'update' has no known invoker
warning: Interface 'TreeSortable' virtual function 'set_sort_func' has no known invoker
warning: Interface 'TreeSortable' virtual function 'set_default_sort_func' has no known invoker
warning: Interface 'Editable' virtual function 'do_insert_text' has no known invoker
warning: Interface 'Editable' virtual function 'do_delete_text' has no known invoker
warning: Interface 'Editable' virtual function 'set_selection_bounds' has no known invoker
warning: Interface 'RecentChooser' virtual function 'get_recent_manager' has no known invoker
warning: Interface 'RecentChooser' virtual function 'set_sort_func' has no known invoker
make[2]: *** No rule to make target `Soup-2.4.gir', needed by `WebKit-1.0.gir'. Stop.
make[2]: Leaving directory `/home/gary/gnome-shell/source/gir-repository/gir'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/gary/gnome-shell/source/gir-repository'
make: *** [all] Error 2
*** error during stage build of gir-repository: ########## Error running make   *** [2/6]


Checked Synaptic for soup-2.4.gir - is this libsoup-2.4 ????

---

### Post by gnomeuser on 2009-05-21
> **RiceMonster said:**
> Because the last version was 2?

The gnome-shell is a proposed component of GNOME 3, it does not define GNOME 3.

---

### Post by Eclipse. on 2009-05-21
> **nolliecrooked said:**
> ok, now it craps out with;

*** Checking out gobject-introspection *** [1/6]
git pull --rebase
Current branch master is up to date.
*** Configuring gobject-introspection *** [1/6]
./autogen.sh --prefix /home/kieran/gnome-shell/install --libdir '/home/kieran/gnome-shell/install/lib'  --disable-static --disable-gtk-doc 
[B]You need to install the gnome-common module and make
sure the gnome-autogen.sh script is in your $PATH.[/B]
*** error during phase configure of gobject-introspection: ########## Error running ./autogen.sh --prefix /home/kieran/gnome-shell/install --libdir '/home/kieran/gnome-shell/install/lib'  --disable-static --disable-gtk-doc  *** [1/6]

  [1] rerun phase configure
  [2] ignore error and continue to build
  [3] give up on module
  [4] start shell
  [5] reload configuration
  [6] go to phase force_checkout
  [7] go to phase clean
  [8] go to phase distclean
choice: 

whats gnome-common module?

gnome-common is a meta-package which contains all the lovely things you need to build gnome stuff.The script is supposed to install all the dependencies you need to build gnome-shell.Make sure you dont have anything like synaptic or update-manager than would block it installing packages then run the script again.I'm pretty sure it installed all the needed dependencies with me.

EDIT: I was bored and decided to have a look at the the code in the script heres the important bit to us.
```

if test x$system = xUbuntu -o x$system = xDebian ; then
  reqd=""
  for pkg in \
    build-essential curl \
    automake bison flex git-core gnome-common gtk-doc-tools \
    libdbus-glib-1-dev libgconf2-dev libgtk2.0-dev libffi-dev \
    libgnome-menu-dev libgnomeui-dev librsvg2-dev libwnck-dev libgl1-mesa-dev \
    mesa-common-dev python-dev libreadline5-dev xulrunner-dev \
    xserver-xephyr libxss-dev \
    libgstreamer0.10-dev gstreamer0.10-plugins-base gstreamer0.10-plugins-good \
    ; do
      if ! dpkg_is_installed $pkg; then
        reqd="$pkg $reqd"
      fi
  done
  if test ! "x$reqd" = x; then
    echo "Please run 'sudo apt-get install $reqd' and try again."
    echo
    exit 1
  fi
fi

```It should install all the stuff you need according to that, very strange.

sudo apt-get install build-essential curl automake bison flex git-core gnome-common gtk-doc-tools libdbus-glib-1-dev libgconf2-dev libgtk2.0-dev libffi-dev libgnome-menu-dev libgnomeui-dev librsvg2-dev libwnck-dev libgl1-mesa-dev mesa-common-dev python-dev libreadline5-dev xulrunner-dev xserver-xephyr libxss-dev libgstreamer0.10-dev gstreamer0.10-plugins-base gstreamer0.10-plugins-good

And you should be good to go.

---

### Post by hanzomon4 on 2009-05-21
> **gnomeuser said:**
> The gnome-shell is a proposed component of GNOME 3, it does not define GNOME 3.

What is Gnome 3? and will the Shell be dolled up any? Currently it looks like same old funky Gnome with a bar on the side.

---

### Post by hyperdude111 on 2009-05-21
For a pre-pre-pre alpha it is not bad, but loads of work is needed before the final release. 

The panels need to be more customizable and it is quite buggy, but the only way is up.

---

