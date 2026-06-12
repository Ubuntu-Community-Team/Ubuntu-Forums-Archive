---
title: "New vte3 (1:0.30.1-2) breaks gnome-terminal"
date: 2011-12-12
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by Harry33 on 2011-12-12
The newest vte3 (1:0.30.1-2) **** upgrade breaks gnome-terminal.

Also people using synaptic need to know that this new vte3 (GTK+3) breaks old vte (GTK+2), which is needed by synaptic. There is an update to vte (GTK+2), however, available:
[https://launchpad.net/ubuntu/precise/+source/vte/1:0.28.2-3ubuntu1](https://launchpad.net/ubuntu/precise/+source/vte/1:0.28.2-3ubuntu1)

The problem is that you cannot install this update, if you haven't installed at the same time the new vte3 (GTK+3), which breaks gnome-terminal.

---

### Post by ventrical on 2011-12-12
> **Harry33 said:**
> The newest vte3 (1:0.30.1-2)  upgrade breaks gnome-terminal.

Also people using synaptic need to know that this new vte3 (GTK+3) breaks old vte (GTK+2), which is needed by synaptic. There is an update to vte (GTK+2), however, available:
[https://launchpad.net/ubuntu/precise/+source/vte/1:0.28.2-3ubuntu1](https://launchpad.net/ubuntu/precise/+source/vte/1:0.28.2-3ubuntu1)

The problem is that you cannot install this update, if you haven't installed at the same time the new vte3 (GTK+3), which breaks gnome-terminal.


@harry33,

Can you be more explicit .. as in <how> do we update (at the same time) vte3(GTK+3) or should we at all??

---

### Post by Harry33 on 2011-12-12
Please do not upgrade neither of those yet (vte, vte3).
However, if you people do not have synaptic installed, you may not have vte (GTK+2) installed either.
I still do not know, woud vte3 then work.

---

### Post by ventrical on 2011-12-12
I have synaptic but cannot find no such file s as vte(n)

---

### Post by sgage on 2011-12-12
> **Harry33 said:**
> Please do not upgrade neither of those yet (vte, vte3).
However, if you people do not have synaptic installed, you may not have vte (GTK+2) installed either.
I still do not know, woud vte3 then work.

Yep, definitely breaks gnome-terminal...

---

### Post by paul_in_london on 2011-12-12
Just been bitten by this. Had to fall back on xterm.

```
paul@precise-64:~$ gnome-terminal
gnome-terminal: symbol lookup error: gnome-terminal: undefined symbol: vte_terminal_set_alternate_screen_scroll

```

---

### Post by ventrical on 2011-12-12
Unbelivable.. I just updated an hour or so ago.. didn't check because I had terminal open. Closed terminal then reopened and  now it's foobarred.

---

### Post by ventrical on 2011-12-12
> **Harry33 said:**
> The newest vte3 (1:0.30.1-2)  upgrade breaks gnome-terminal.

Also people using synaptic need to know that this new vte3 (GTK+3) breaks old vte (GTK+2), which is needed by synaptic. There is an update to vte (GTK+2), however, available:
[https://launchpad.net/ubuntu/precise/+source/vte/1:0.28.2-3ubuntu1](https://launchpad.net/ubuntu/precise/+source/vte/1:0.28.2-3ubuntu1)

The problem is that you cannot install this update, if you haven't installed at the same time the new vte3 (GTK+3), which breaks gnome-terminal.


Has there been no bug report over this harry33?

---

### Post by paul_in_london on 2011-12-12
Fixed now with latest updates:

```
paul@precise-64:~$ sudo aptitude full-upgrade
The following packages will be upgraded: 
  gir1.2-vte-2.90 libglib2.0-data libvte-2.90-9 libvte-2.90-common
```

---

### Post by matt_symes on 2011-12-12
I've been using xterm as well.

---

### Post by paul_in_london on 2011-12-12
> **matt_symes said:**
> I've been using xterm as well.

As I say, you can go back to gnome-terminal mate. It's working again now. :)

---

### Post by Harry33 on 2011-12-13
This bug (903401) has been fixed:

[https://bugs.launchpad.net/ubuntu/+source/gnome-terminal/+bug/903401](https://bugs.launchpad.net/ubuntu/+source/gnome-terminal/+bug/903401)

Here is the update:
[https://launchpad.net/ubuntu/precise/+source/vte3/1:0.30.1-2ubuntu2](https://launchpad.net/ubuntu/precise/+source/vte3/1:0.30.1-2ubuntu2)

---

