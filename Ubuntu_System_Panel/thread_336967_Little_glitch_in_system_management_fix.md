---
title: "Little glitch in system management fix"
date: 2007-01-12
forum: Ubuntu System Panel
---

### Post by ADRez on 2007-01-12
If you notice Control Panel is not aligned as Lock screen and Quit, it is a little bit at the left.
I have insert after line 111 this line for fixing it:

<property name="width_request">40</property>

---

### Post by chanders on 2007-01-12
> **ADRez said:**
> If you notice Control Panel is not aligned as Lock screen and Quit, it is a little bit at the left.
I have insert after line 111 this line for fixing it:

<property name="width_request">40</property>

Fixed!

---

### Post by ardchoille42 on 2007-01-12
> **ADRez said:**
> If you notice Control Panel is not aligned as Lock screen and Quit, it is a little bit at the left.
I have insert after line 111 this line for fixing it:

<property name="width_request">40</property>

Ok, I am assuming you mean that the above line you gave is to be the new line 112 like this:

```

111		if not self.client.dir_exists (self.gconf_dir):
112                        <property name="width_request">40</property>
113			self.client.add_dir (self.gconf_dir, gconf.CLIENT_PRELOAD_NONE)
114
115		self.client.add_dir('/desktop/gnome/screen/default/0', gconf.CLIENT_PRELOAD_NONE)

```

Is that correct? If so, when I restart sup, it crashes (my first usp crash) and it starts up normally when I remove that line again. I'm using USP .41 on Ubuntu 6.01.6 LTS Dapper.

---

### Post by ADRez on 2007-01-12
That's for USP2!!
And the file to edit is system_management.glade, not the .py one.
This is the part of the code where I included it:

		  <child>
		    <widget class="GtkImage" id="image2">
		      <property name="width_request">40</property>
		      <property name="visible">True</property>
		      <property name="icon_size">1</property>
		      <property name="icon_name">gnome-control-center</property>
		      <property name="xalign">0.5</property>
		      <property name="yalign">0.5</property>
		      <property name="xpad">10</property>
		      <property name="ypad">0</property>
		    </widget>
		    <packing>
		      <property name="padding">0</property>
		      <property name="expand">False</property>
		      <property name="fill">True</property>
		    </packing>
		  </child>

---

### Post by ardchoille42 on 2007-01-12
D'oh! I'm an idiot.. I should have seen from the syntax that it didn't go into a .py file. Besides, I don't have USP2, maybe I should install it.
Oh well, live and learn :)

---

