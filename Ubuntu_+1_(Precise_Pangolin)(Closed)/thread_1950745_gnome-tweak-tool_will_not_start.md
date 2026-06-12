---
title: "gnome-tweak-tool will not start"
date: 2012-04-01
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by mdhollis on 2012-04-01
Can anyone make sense of this?

```
matthew@precise:~$ gnome-tweak-tool

(gnome-tweak-tool:2334): GLib-GIO-ERROR **: Settings schema 'org.gnome.shell.extensions.user-theme' is not installed

Trace/breakpoint trap (core dumped)
```

I have a couple of extensions installed from [https://extensions.gnome.org](https://extensions.gnome.org) including the user-theme extension.  Disabling it has no effect. gnome-tweak-tool will not start.  I tried to purge and re-install and I am completely up to date......

It actually runs in unity but not gnome-shell........weird....

---

### Post by rburkartjo on 2012-04-01
working fine on my end

---

### Post by lucazade on 2012-04-01
try to remove user-theme folder in .local/share/gnome-shell/extensions and restart the app

---

### Post by mdhollis on 2012-04-01
> **lucazade said:**
> try to remove user-theme folder in .local/share/gnome-shell/extensions and restart the app

That did the trick......thanks!

---

### Post by m314 on 2012-04-12
> **mdhollis said:**
> That did the trick......thanks!
But this does not resolve the issue! The main issue is that the User Theme extension breaks gnome-tweak-tool.

---

### Post by macstevejb on 2012-04-13
try using the shell extensions provided by the webupd8 team via their ppa:

[http://www.webupd8.org/2012/03/official-gnome-shell-extensions-weather.html](http://www.webupd8.org/2012/03/official-gnome-shell-extensions-weather.html)

The user theme extension is included which I can confirm does work with the gnome-tweak-tool.

HTH

Regards, :p

---

### Post by SWoRD-Jr on 2012-04-13
The solution if you installed the user-theme extension from the gnome website is:

```
sudo cp  /home/USERNAME/.local/share/gnome-shell/extensions/user-theme@gnome-shell-extensions.gcampax.github.com/schemas/org.gnome.shell.extensions.user-theme.gschema.xml  /usr/share/glib-2.0/schemas

sudo glib-compile-schemas /usr/share/glib-2.0/schemas
```Replace USERNAME with your login name. Thanks to cluke009 for this tip on the extensions website.

---

