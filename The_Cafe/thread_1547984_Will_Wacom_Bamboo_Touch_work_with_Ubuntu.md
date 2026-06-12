---
title: "Will Wacom Bamboo Touch work with Ubuntu?"
date: 2010-08-07
forum: The Cafe
---

### Post by TheNerdAL on 2010-08-07
So I sold my PSP and games to get a graphics tablet to draw my cartoons for my cartoon show and I want to get the Wacom Bamboo Touch (is that a good graphics tablet?). I was wondering if it would work like out of the box? Thanks. :)

---

### Post by NCLI on 2010-08-07
The Bamboo is OK, but it's really the most low-end you can get from Wacom. It's not bad, just not really good either.
If you want a good tablet, buy an Intous.

Anyway, both should work just fine with Ubuntu.

---

### Post by Favux on 2010-08-07
Hi TheNerdAL,

Not out of the box in Lucid.  But the set up isn't hard.  See the [Bamboo HOW TO]("http://ubuntuforums.org/showpost.php?p=9496609&postcount=1").

And you don't want the Touch, since it only has touch and no Pen.  At least the Bamboo Pen and Touch, or Craft, or Fun.  If you're doing graphics you might want the Fun since it has the biggest drawing area.

---

### Post by TheNerdAL on 2010-08-07
> **NCLI said:**
> The Bamboo is OK, but it's really the most low-end you can get from Wacom. It's not bad, just not really good either.
If you want a good tablet, buy an Intous.

Anyway, both should work just fine with Ubuntu.

It's a bit over my budget. :P Would the Craft be better?

---

### Post by TheNerdAL on 2010-08-07
Or are there any other graphics tablet besides the Wacom ones that you'd recommend?

---

### Post by Legendary_Bibo on 2010-08-07
Why not get the Bamboo Pen? It's one actually meant for drawing, I even made a shell script to set up the drivers for it.

---

### Post by Legendary_Bibo on 2010-08-07
> **TheNerdAL said:**
> Or are there any other graphics tablet besides the Wacom ones that you'd recommend?

Wacom seems to be the most linux friendly.

---

### Post by TheNerdAL on 2010-08-07
> **Legendary_Bibo said:**
> Wacom seems to be the most linux friendly.

Yeah, I got the Wacom Bamboo Craft but it's not working.

---

### Post by Favux on 2010-08-07
Did you follow the link (click on it) to the HOW to I gave you?

---

### Post by Legendary_Bibo on 2010-08-07
> **TheNerdAL said:**
> Yeah, I got the Wacom Bamboo Craft but it's not working.

Well try this shell script then, also in /etc/modules add the word 'wacom' without the quotations on a new line so it's probed at boot up.

---

### Post by TheNerdAL on 2010-08-07
> **Favux said:**
> Did you follow the link (click on it) to the HOW to I gave you?

Do I do everything in the page?

---

### Post by Favux on 2010-08-07
You don't have to.  You'll want to do I. and II.  That will get it working.  You can skip III. since it works with the default 10-wacom.conf.  That's for if you want to change something.  And you'll probably want to install a xsetwacom script (.xsetwacom.sh) IV. since it let's you control things like pressure etc.  Whether you want a touch toggle script is up to you.

So I., II., and IV.  Follow a step at a time.  It'll go quick.

---

### Post by TheNerdAL on 2010-08-07
> **Favux said:**
> You don't have to.  You'll want to do I. and II.  That will get it working.  You can skip III. since it works with the default 10-wacom.conf.  That's for if you want to change something.  And you'll probably want to install a xsetwacom script (.xsetwacom.sh) IV. since it let's you control things like pressure etc.  Whether you want a touch toggle script is up to you.

So I., II., and IV.  Follow a step at a time.  It'll go quick.

What attached file for IV? I don't know what it is. :P

EDIT: Nevermind, I think I got it. It works now but when I use my finger to control the cursor, it doesn't work smoothly, it like stops when I'm trying to move it. ):

EDIT: Now when I right click, it doesn't give me the little menu. ):

---

### Post by Favux on 2010-08-07
You may be one of those who has problems with touch.  Did you reboot a couple of times?  For a fix see the big blue heading near the top and follow the link to post #110.

By right click problem, do you mean with touch or stylus?

---

### Post by TheNerdAL on 2010-08-07
> **Favux said:**
> You may be one of those who has problems with touch.  For a fix see the big blue heading near the top and follow the link to post #110.

By right click problem, do you mean with touch?

With mouse. The scroll click got change to right click.

---

### Post by TheNerdAL on 2010-08-07
I don't get none of this: [http://ubuntuforums.org/showpost.php?p=9675615&postcount=110](http://ubuntuforums.org/showpost.php?p=9675615&postcount=110)

---

### Post by Favux on 2010-08-07
How is touch for you now?  You only need to do post #110 if it isn't working.  One of the developers (Chris) knows about the problem, so a fix will probably appear in xf86-input-wacom in a week or so.

Nothing you've done should affect a mouse.  Is it a plug in usb mouse?

---

### Post by TheNerdAL on 2010-08-07
> **Favux said:**
> How is touch for you now?  You only need to do post #110 if it isn't working.  One of the developers (Chris) knows about the problem, so a fix will probably appear in xf86-input-wacom in a week or so.

Nothing you've done should affect a mouse.  Is it a plug in usb mouse?

Touch works, it just isn't smooth like it stops working a few times when I use my finger. 

The mouse is USB but I noticed a change in it when I did step IV...or when I think I did it right.

---

### Post by Favux on 2010-08-07
Well the Bamboo doesn't have a wacom tablet mouse so xsetwacom commands won't affect a logitech or MS or whatever mouse.
> Touch works, it just isn't smooth like it stops working a few times when I use my finger.

OK, but you got it for the stylus to draw cartoons right?  How is the stylus working?  Do you have pressure?

Like I said if you still have problems with touch a fix is coming.  Or if you want to try the fix in post #110 we could walk through that.  But maybe let the dust settle and see if touch is really a problem?

---

### Post by TheNerdAL on 2010-08-07
> **Favux said:**
> Well the Bamboo doesn't have a wacom tablet mouse so xsetwacom commands won't affect a logitech or MS or whatever mouse.

OK, but you got it for the stylus to draw cartoons right?  How is the stylus working?  Do you have pressure?

Like I said if you still have problems with touch a fix is coming.  Or if you want to try the fix in post #110 we could walk through that.  But maybe let the dust settle and see if touch is really a problem?

I want to try post #110. MWahahaha!! I sound like I'm doing an experiment or something.

But how do I fix my mouse then? :( I think it's because I messed up step IV because I didn't understand it so I untarred it and just ran both .sh files. O:

---

### Post by Favux on 2010-08-07
> I think it's because I messed up step IV because I didn't understand it so I untarred it and just ran both .sh files.
Well that could be a problem.  Only the wacom.conf .sh should be applied since you are using the 10-wacom.conf not the xorg.conf.  Look at the top of it.  You need to run 'xinput --list' in a terminal to find out the "Device names" to use in your version of the script.  Follow?  Once that's working reboot a few times and see what happens.

---

### Post by Legendary_Bibo on 2010-08-07
How come no one ever uses my shell script? :mad:

I never tried to get pressure to work because I didn't have a need to, but you could do that afterwards.

---

### Post by TheNerdAL on 2010-08-07
I get this: 
```
adrian@adrian-desktop:~$ xinput --list
&#9121; Virtual core pointer                    	id=2	[master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer              	id=4	[slave  pointer  (2)]
&#9116;   &#8627; Fellowes Fellowes 5 Button              	id=9	[slave  pointer  (2)]
&#9116;   &#8627; Wacom Bamboo Craft Pen eraser           	id=10	[slave  pointer  (2)]
&#9116;   &#8627; Wacom Bamboo Craft Pen stylus           	id=11	[slave  pointer  (2)]
&#9116;   &#8627; Wacom Bamboo Craft Finger pad           	id=12	[slave  pointer  (2)]
&#9116;   &#8627; Wacom Bamboo Craft Finger touch         	id=13	[slave  pointer  (2)]
&#9116;   &#8627; Macintosh mouse button emulation        	id=15	[slave  pointer  (2)]
&#9123; Virtual core keyboard                   	id=3	[master keyboard (2)]
    &#8627; Virtual core XTEST keyboard             	id=5	[slave  keyboard (3)]
    &#8627; Power Button                            	id=6	[slave  keyboard (3)]
    &#8627; Power Button                            	id=7	[slave  keyboard (3)]
    &#8627; Sleep Button                            	id=8	[slave  keyboard (3)]
    &#8627; AT Translated Set 2 keyboard            	id=14	[slave  keyboard (3)]
adrian@adrian-desktop:~$ 


```

---

### Post by TheNerdAL on 2010-08-07
> **Legendary_Bibo said:**
> How come no one ever uses my shell script? :mad:

I never tried to get pressure to work because I didn't have a need to, but you could do that afterwards.

I used it..well...at least I think I did. 

I messed up my mouse!!!!!!!!!!!! :(

---

### Post by Favux on 2010-08-08
Well what does your .xsetwacom.sh script look like now?


Hi Legendary_Bibo,

You got me.  Have you kept it up to date?

---

### Post by TheNerdAL on 2010-08-08
> **Favux said:**
> Well what does your .xsetwacom.sh script look like now?


Hi Legendary_Bibo,

You got me.  Have you kept it up to date?

How do I determine that? Sorry, I'm new at using terminal, lol.

---

### Post by Legendary_Bibo on 2010-08-08
> **Favux said:**
> Well what does your .xsetwacom.sh script look like now?


Hi Legendary_Bibo,

You got me.  Have you kept it up to date?

Yep, I check the site from time to time, and just change the numbers.

---

### Post by Favux on 2010-08-08
If you followed the directions it is a hidden file in your home directory.  So you want to tell Places to show hidden files (View > Show Hidden Files).  Then right click on it and open with gedit.  Remember there should only be one .xsetwacom.sh.

I've noticed with the last few kernel updates that right click is missing from the mouse after the first restart.  The middle mouse click actually becomes the right click.  Another restart has cleared it up for me.  That's why I keep telling you to restart a couple of times.  Before you did the Bamboo HOW TO did you let update manager install a new Lucid kernel?

---

### Post by TheNerdAL on 2010-08-08
> **Favux said:**
> If you followed the directions it is a hidden file in your home directory.  So you want to tell Places to show hidden files (View > Show Hidden Files).  Then right click on it and open with gedit.  Remember there should only be one .xsetwacom.sh.

I've noticed with the last few kernel updates that right click is missing from the mouse after the first restart.  The middle mouse click actually becomes the right click.  Another restart has cleared it up for me.  That's why I keep telling you to restart a couple of times.  Before you did the Bamboo HOW TO did you let update manager install a new Lucid kernel?

I shall restart and see if that works. But let's try to fix the touch problem while I restart lol.

---

### Post by TheNerdAL on 2010-08-08
Restart fixed the problem. :) Lol, thanks but when I move the cursor using the graphics tablet, it still stops sometimes while I'm moving my fingers. :(

---

### Post by Favux on 2010-08-08
Well you use Places to Navigate to the xf86-input-wacom directory.  The folder should be on your Desktop.  Then you go into the src directory.  Then you open up the file wcmCommon.c in gedit.  In gedit you have the option to show line numbers (Edit > Preferences - check Display line numbers).  Go to about line # 34 and change:
```
#define BAMBOO_TOUCH_JUMPED 30
```
to
```
#define BAMBOO_TOUCH_JUMPED 300
```
Save and close.

Open a terminal:  Appications > Accesories > terminal

Enter in it:
```
cd ./Desktop

cd xf86-input-wacom

make clean

./autogen.sh --prefix=/usr

make

sudo make install

(Now reboot.)
```
Basically you're repeating II., at least the parts you now need.

---

### Post by TheNerdAL on 2010-08-08
Mine doesn't have that in line 34. This is what mine looks like: 
```
/*
 * Copyright 2009 Red Hat, Inc.
 *
 * This program is free software; you can redistribute it and/or
 * modify it under the terms of the GNU General Public License
 * as published by the Free Software Foundation; either version 2
 * of the License, or (at your option) any later version.
 *
 * This program is distributed in the hope that it will be useful,
 * but WITHOUT ANY WARRANTY; without even the implied warranty of
 * MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the
 * GNU General Public License for more details.
 *
 * You should have received a copy of the GNU General Public License
 * along with this program; if not, write to the Free Software
 * Foundation, Inc., 59 Temple Place - Suite 330, Boston, MA 02111-1307, USA.
 */

#ifdef HAVE_CONFIG_H
#define WACOM_TOOLS
#include "config.h"
#endif

#include <wacom-properties.h>
#include "Xwacom.h"

#include <stdio.h>
#include <stdarg.h>
#include <ctype.h>
#include <stdlib.h>
#include <getopt.h>
#include <string.h>
#include <math.h>
#include <X11/Xlib.h>
#include <X11/Xatom.h>
#include <X11/extensions/XInput.h>
#include <X11/XKBlib.h>

#define TRACE(...) \
	if (verbose) fprintf(stderr, "... " __VA_ARGS__)

#define ArrayLength(a) (sizeof(a) / (sizeof((a)[0])))

static int verbose = False;

enum printformat {
	FORMAT_DEFAULT,
	FORMAT_XORG_CONF,
	FORMAT_SHELL
};

enum prop_flags {
	PROP_FLAG_BOOLEAN = 1,
	PROP_FLAG_READONLY = 2,
	PROP_FLAG_WRITEONLY = 4
};


/**
 * How this works:
 * Each parameter supported by xsetwacom has a struct param_t in the global
 * parameters[] array.
 * For 'standard' parameters that just modify a property, the prop_* fields
 * are set to the matching property, format and offset. The get() function
 * then handles the retrieval  of the property, the set() function handles
 * the modification of the property.
 *
 * For parameters that need more than just triggering a property, the
 * set_func and get_func point to the matching function to modify that
 * particular parameter. example are the ButtonX parameters that call
 * XSetDeviceButtonMapping instead of triggering a property.
 *
 * device_name is filled in automatically and just used to pass around the
 * device name (since the XDevice* doesn't store this info). printformat is
 * a flag that changes the output required, so that the -c and -s
 * commandline arguments work.
 */

typedef struct _param
{
	const char *name;	/* param name as specified by the user */
	const char *desc;	/* description */
	const char *prop_name;	/* property name */
	const int prop_format;	/* property format */
	const int prop_offset;	/* offset (index) into the property values */
	const unsigned int prop_flags;
	void (*set_func)(Display *dpy, XDevice *dev, struct _param *param, int argc, char **argv); /* handler function, if appropriate */
	void (*get_func)(Display *dpy, XDevice *dev, struct _param *param, int argc, char **argv); /* handler function for getting, if appropriate */

	/* filled in by get() */
	char *device_name;
	enum printformat printformat;
} param_t;

/* get_func/set_func calls for special parameters */
static void map_button(Display *dpy, XDevice *dev, param_t *param, int argc, char **argv);
static void set_mode(Display *dpy, XDevice *dev, param_t *param, int argc, char **argv);
static void get_mode(Display *dpy, XDevice *dev, param_t *param, int argc, char **argv);
static void get_presscurve(Display *dpy, XDevice *dev, param_t *param, int argc, char **argv);
static void get_button(Display *dpy, XDevice *dev, param_t *param, int argc, char **argv);
static void set_rotate(Display *dpy, XDevice *dev, param_t *param, int argc, char **argv);
static void get_rotate(Display *dpy, XDevice *dev, param_t *param, int argc, char **argv);
static void set_twinview(Display *dpy, XDevice *dev, param_t *param, int argc, char **argv);
static void get_twinview(Display *dpy, XDevice *dev, param_t *param, int argc, char **argv);
static void set_xydefault(Display *dpy, XDevice *dev, param_t *param, int argc, char **argv);
static void get_all(Display *dpy, XDevice *dev, param_t *param, int argc, char **argv);
static void get_param(Display *dpy, XDevice *dev, param_t *param, int argc, char **argv);

static param_t parameters[] =
{
	{
		.name = "TopX",
		.desc = "Bounding rect left coordinate in tablet units. ",
		.prop_name = WACOM_PROP_TABLET_AREA,
		.prop_format = 32,
		.prop_offset = 0,
	},
	{
		.name = "TopY",
		.desc = "Bounding rect top coordinate in tablet units . ",
		.prop_name = WACOM_PROP_TABLET_AREA,
		.prop_format = 32,
		.prop_offset = 1,
	},
	{
		.name = "BottomX",
		.desc = "Bounding rect right coordinate in tablet units. ",
		.prop_name = WACOM_PROP_TABLET_AREA,
		.prop_format = 32,
		.prop_offset = 2,
	},
	{
		.name = "BottomY",
		.desc = "Bounding rect bottom coordinate in tablet units. ",
		.prop_name = WACOM_PROP_TABLET_AREA,
		.prop_format = 32,
		.prop_offset = 3,
	},
	{
		.name = "Button1",
		.desc = "X11 event to which button 1 should be mapped. ",
		.set_func = map_button,
		.get_func = get_button,
	},
	{
		.name = "Button2",
		.desc = "X11 event to which button 2 should be mapped. ",
		.set_func = map_button,
		.get_func = get_button,
	},
	{
		.name = "Button3",
		.desc = "X11 event to which button 3 should be mapped. ",
		.set_func = map_button,
		.get_func = get_button,
	},
	{
		.name = "Button4",
		.desc = "X11 event to which button 4 should be mapped. ",
		.set_func = map_button,
		.get_func = get_button,
	},
	{
		.name = "Button5",
		.desc = "X11 event to which button 5 should be mapped. ",
		.set_func = map_button,
		.get_func = get_button,
	},
	{
		.name = "Button6",
		.desc = "X11 event to which button 6 should be mapped. ",
		.set_func = map_button,
		.get_func = get_button,
	},
	{
		.name = "Button7",
		.desc = "X11 event to which button 7 should be mapped. ",
		.set_func = map_button,
		.get_func = get_button,
	},
	{
		.name = "Button8",
		.desc = "X11 event to which button 8 should be mapped. ",
		.set_func = map_button,
		.get_func = get_button,
	},
	{
		.name = "Button9",
		.desc = "X11 event to which button 9 should be mapped. ",
		.set_func = map_button,
		.get_func = get_button,
	},
	{
		.name = "Button10",
		.desc = "X11 event to which button 10 should be mapped. ",
		.set_func = map_button,
		.get_func = get_button,
	},
	{
		.name = "Button11",
		.desc = "X11 event to which button 11 should be mapped. ",
		.set_func = map_button,
		.get_func = get_button,
	},
	{
		.name = "Button12",
		.desc = "X11 event to which button 12 should be mapped. ",
		.set_func = map_button,
		.get_func = get_button,
	},
	{
		.name = "Button13",
		.desc = "X11 event to which button 13 should be mapped. ",
		.set_func = map_button,
		.get_func = get_button,
	},
	{
		.name = "Button14",
		.desc = "X11 event to which button 14 should be mapped. ",
		.set_func = map_button,
		.get_func = get_button,
	},
	{
		.name = "Button15",
		.desc = "X11 event to which button 15 should be mapped. ",
		.set_func = map_button,
		.get_func = get_button,
	},
	{
		.name = "Button16",
		.desc = "X11 event to which button 16 should be mapped. ",
		.set_func = map_button,
		.get_func = get_button,
	},
	{
		.name = "Button17",
		.desc = "X11 event to which button 17 should be mapped. ",
		.set_func = map_button,
		.get_func = get_button,
	},
	{
		.name = "Button18",
		.desc = "X11 event to which button 18 should be mapped. ",
		.set_func = map_button,
		.get_func = get_button,
	},
	{
		.name = "Button19",
		.desc = "X11 event to which button 19 should be mapped. ",
		.set_func = map_button,
		.get_func = get_button,
	},
	{
		.name = "Button20",
		.desc = "X11 event to which button 20 should be mapped. ",
		.set_func = map_button,
		.get_func = get_button,
	},
	{
		.name = "Button21",
		.desc = "X11 event to which button 21 should be mapped. ",
		.set_func = map_button,
		.get_func = get_button,
	},
	{
		.name = "Button22",
		.desc = "X11 event to which button 22 should be mapped. ",
		.set_func = map_button,
		.get_func = get_button,
	},
	{
		.name = "Button23",
		.desc = "X11 event to which button 23 should be mapped. ",
		.set_func = map_button,
		.get_func = get_button,
	},
	{
		.name = "Button24",
		.desc = "X11 event to which button 24 should be mapped. ",
		.set_func = map_button,
		.get_func = get_button,
	},
	{
		.name = "Button25",
		.desc = "X11 event to which button 25 should be mapped. ",
		.set_func = map_button,
		.get_func = get_button,
	},
	{
		.name = "Button26",
		.desc = "X11 event to which button 26 should be mapped. ",
		.set_func = map_button,
		.get_func = get_button,
	},
	{
		.name = "Button27",
		.desc = "X11 event to which button 27 should be mapped. ",
		.set_func = map_button,
		.get_func = get_button,
	},
	{
		.name = "Button28",
		.desc = "X11 event to which button 28 should be mapped. ",
		.set_func = map_button,
		.get_func = get_button,
	},
	{
		.name = "Button29",
		.desc = "X11 event to which button 29 should be mapped. ",
		.set_func = map_button,
		.get_func = get_button,
	},
	{
		.name = "Button30",
		.desc = "X11 event to which button 30 should be mapped. ",
		.set_func = map_button,
		.get_func = get_button,
	},
	{
		.name = "Button31",
		.desc = "X11 event to which button 31 should be mapped. ",
		.set_func = map_button,
		.get_func = get_button,
	},
	{
		.name = "Button32",
		.desc = "X11 event to which button 32 should be mapped. ",
		.set_func = map_button,
		.get_func = get_button,
	},
	{
		.name = "DebugLevel",
		.desc = "Level of debugging trace for individual devices, "
		"default is 0 (off). ",
		.prop_name = WACOM_PROP_DEBUGLEVELS,
		.prop_format = 8,
		.prop_offset = 0,
	},
	{
		.name = "CommonDBG",
		.desc = "Level of debugging statements applied to all devices "
		"associated with the same tablet. default is 0 (off). ",
		.prop_name = WACOM_PROP_DEBUGLEVELS,
		.prop_format = 8,
		.prop_offset = 1,
	},
	{
		.name = "Suppress",
		.desc = "Number of points trimmed, default is 2. ",
		.prop_name = WACOM_PROP_SAMPLE,
		.prop_format = 32,
		.prop_offset = 1,
	},
	{
		.name = "RawSample",
		.desc = "Number of raw data used to filter the points, "
		"default is 4. ",
		.prop_name = WACOM_PROP_SAMPLE,
		.prop_format = 32,
		.prop_offset = 0,
	},
	{
		.name = "Screen_No",
		.desc = "Sets/gets screen number the tablet is mapped to, "
		"default is -1. ",
		.prop_name = WACOM_PROP_DISPLAY_OPTS,
		.prop_format = 8,
		.prop_offset = 0,
	},
	{
		.name = "PressCurve",
		.desc = "Bezier curve for pressure (default is 0 0 100 100). ",
		.prop_name = WACOM_PROP_PRESSURECURVE,
		.prop_format = 32,
		.prop_offset = 0,
		.get_func = get_presscurve,
	},
	{
		.name = "TwinView",
		.desc = "Sets the mapping to TwinView horizontal/vertical/none. "
		"Values = none, vertical, horizontal (default is none).",
		.prop_name = WACOM_PROP_DISPLAY_OPTS,
		.prop_format = 8,
		.prop_offset = 1,
		.get_func = get_twinview,
		.set_func = set_twinview,
	},
	{
		.name = "Mode",
		.desc = "Switches cursor movement mode (default is absolute/on). ",
		.set_func = set_mode,
		.get_func = get_mode,
	},
	{
		.name = "TPCButton",
		.desc = "Turns on/off Tablet PC buttons. "
		"default is off for regular tablets, "
		"on for Tablet PC. ",
		.prop_name = WACOM_PROP_HOVER,
		.prop_format = 8,
		.prop_offset = 0,
		.prop_flags = PROP_FLAG_BOOLEAN
	},
	{
		.name = "Touch",
		.desc = "Turns on/off Touch events (default is enable/on). ",
		.prop_name = WACOM_PROP_TOUCH,
		.prop_format = 8,
		.prop_offset = 0,
		.prop_flags = PROP_FLAG_BOOLEAN
	},
	{
		.name = "Gesture",
		.desc = "Turns on/off multi-touch gesture events "
		"(default is enable/on). ",
		.prop_name = WACOM_PROP_ENABLE_GESTURE,
		.prop_format = 8,
		.prop_offset = 0,
		.prop_flags = PROP_FLAG_BOOLEAN
	},
	{
		.name = "ZoomDistance",
		.desc = "Minimum distance for a zoom gesture "
		"(default is 50). ",
		.prop_name = WACOM_PROP_GESTURE_PARAMETERS,
		.prop_format = 32,
		.prop_offset = 0,
	},
	{
		.name = "ScrollDistance",
		.desc = "Minimum motion before sending a scroll gesture "
		"(default is 20). ",
		.prop_name = WACOM_PROP_GESTURE_PARAMETERS,
		.prop_format = 32,
		.prop_offset = 0,
	},
	{
		.name = "TapTime",
		.desc = "Minimum time between taps for a right click "
		"(default is 250). ",
		.prop_name = WACOM_PROP_GESTURE_PARAMETERS,
		.prop_format = 32,
		.prop_offset = 0,
	},
	{
		.name = "Capacity",
		.desc = "Touch sensitivity level (default is 3, "
		"-1 for none capacitive tools).",
		.prop_name = WACOM_PROP_CAPACITY,
		.prop_format = 32,
		.prop_offset = 0,
	},
	{
		.name = "CursorProx",
		.desc = "Sets cursor distance for proximity-out "
		"in distance from the tablet.  "
		"(default is 10 for Intuos series, "
		"42 for Graphire series).",
		.prop_name = WACOM_PROP_PROXIMITY_THRESHOLD,
		.prop_format = 32,
		.prop_offset = 0,
	},
	{
		.name = "Rotate",
		.desc = "Sets the rotation of the tablet. "
		"Values = NONE, CW, CCW, HALF (default is NONE).",
		.prop_name = WACOM_PROP_ROTATION,
		.set_func = set_rotate,
		.get_func = get_rotate,
	},
	{
		.name = "RelWUp",
		.desc = "X11 event to which relative wheel up should be mapped. ",
		.prop_name = WACOM_PROP_WHEELBUTTONS,
		.prop_format = 8,
		.prop_offset = 0,
	},
	{
		.name = "RelWDn",
		.desc = "X11 event to which relative wheel down should be mapped. ",
		.prop_name = WACOM_PROP_WHEELBUTTONS,
		.prop_format = 8,
		.prop_offset = 1,
	},
	{
		.name = "AbsWUp",
		.desc = "X11 event to which absolute wheel up should be mapped. ",
		.prop_name = WACOM_PROP_WHEELBUTTONS,
		.prop_format = 8,
		.prop_offset = 2,
	},
	{
		.name = "AbsWDn",
		.desc = "X11 event to which absolute wheel down should be mapped. ",
		.prop_name = WACOM_PROP_WHEELBUTTONS,
		.prop_format = 8,
		.prop_offset = 3,
	},
	{
		.name = "StripLUp",
		.desc = "X11 event to which left strip up should be mapped. ",
		.prop_name = WACOM_PROP_STRIPBUTTONS,
		.prop_format = 8,
		.prop_offset = 0,
	},
	{
		.name = "StripLDn",
		.desc = "X11 event to which left strip down should be mapped. ",
		.prop_name = WACOM_PROP_STRIPBUTTONS,
		.prop_format = 8,
		.prop_offset = 1,
	},
	{
		.name = "StripRUp",
		.desc = "X11 event to which right strip up should be mapped. ",
		.prop_name = WACOM_PROP_STRIPBUTTONS,
		.prop_format = 8,
		.prop_offset = 2,
	},
	{
		.name = "StripRDn",
		.desc = "X11 event to which right strip down should be mapped. ",
		.prop_name = WACOM_PROP_STRIPBUTTONS,
		.prop_format = 8,
		.prop_offset = 3,
	},
	{
		.name = "TVResolution0",
		.desc = "Sets MetaModes option for TwinView Screen 0. ",
		.prop_name = WACOM_PROP_TWINVIEW_RES,
		.prop_format = 32,
		.prop_offset = 0,
	},
	{
		.name = "TVResolution1",
		.desc = "Sets MetaModes option for TwinView Screen 1. ",
		.prop_name = WACOM_PROP_TWINVIEW_RES,
		.prop_format = 32,
		.prop_offset = 1,
	},
	{
		.name = "RawFilter",
		.desc = "Enables and disables filtering of raw data, "
		"default is true/on.",
		.prop_name = WACOM_PROP_SAMPLE,
		.prop_format = 8,
		.prop_offset = 0,
		.prop_flags = PROP_FLAG_BOOLEAN
	},
	{
		.name = "ClickForce",
		.desc = "Sets tip/eraser pressure threshold "
		"(default is 409)",
		.prop_name = WACOM_PROP_PRESSURE_THRESHOLD,
		.prop_format = 32,
		.prop_offset = 0,
	},
	{
		.name = "xyDefault",
		.desc = "Resets the bounding coordinates to default in tablet units. ",
		.prop_name = WACOM_PROP_TABLET_AREA,
		.prop_format = 32,
		.prop_offset = 0,
		.prop_flags = PROP_FLAG_WRITEONLY,
		.set_func = set_xydefault,
	},
	{
		.name = "mmonitor",
		.desc = "Turns on/off across monitor movement in "
		"multi-monitor desktop, default is on ",
		.prop_name = WACOM_PROP_DISPLAY_OPTS,
		.prop_format = 8,
		.prop_offset = 2,
	},
	{
		.name = "STopX0",
		.desc = "Screen 0 left coordinate in pixels. ",
		.prop_name = WACOM_PROP_SCREENAREA,
		.prop_format = 32,
		.prop_offset = 0,
		.prop_flags = PROP_FLAG_READONLY
	},
	{
		.name = "STopY0",
		.desc = "Screen 0 top coordinate in pixels. ",
		.prop_name = WACOM_PROP_SCREENAREA,
		.prop_format = 32,
		.prop_offset = 1,
		.prop_flags = PROP_FLAG_READONLY
	},
	{
		.name = "SBottomX0",
		.desc = "Screen 0 right coordinate in pixels. ",
		.prop_name = WACOM_PROP_SCREENAREA,
		.prop_format = 32,
		.prop_offset = 2,
		.prop_flags = PROP_FLAG_READONLY
	},
	{
		.name = "SBottomY0",
		.desc = "Screen 0 bottom coordinate in pixels. ",
		.prop_name = WACOM_PROP_SCREENAREA,
		.prop_format = 32,
		.prop_offset = 3,
		.prop_flags = PROP_FLAG_READONLY
	},
	{
		.name = "STopX1",
		.desc = "Screen 1 left coordinate in pixels. ",
		.prop_name = WACOM_PROP_SCREENAREA,
		.prop_format = 32,
		.prop_offset = 4,
		.prop_flags = PROP_FLAG_READONLY
	},
	{
		.name = "STopY1",
		.desc = "Screen 1 top coordinate in pixels. ",
		.prop_name = WACOM_PROP_SCREENAREA,
		.prop_format = 32,
		.prop_offset = 5,
		.prop_flags = PROP_FLAG_READONLY
	},
	{
		.name = "SBottomX1",
		.desc = "Screen 1 right coordinate in pixels. ",
		.prop_name = WACOM_PROP_SCREENAREA,
		.prop_format = 32,
		.prop_offset = 6,
		.prop_flags = PROP_FLAG_READONLY
	},
	{
		.name = "SBottomY1",
		.desc = "Screen 1 bottom coordinate in pixels. ",
		.prop_name = WACOM_PROP_SCREENAREA,
		.prop_format = 32,
		.prop_offset = 7,
		.prop_flags = PROP_FLAG_READONLY
	},
	{
		.name = "STopX2",
		.desc = "Screen 2 left coordinate in pixels. ",
		.prop_name = WACOM_PROP_SCREENAREA,
		.prop_format = 32,
		.prop_offset = 8,
		.prop_flags = PROP_FLAG_READONLY
	},
	{
		.name = "STopY2",
		.desc = "Screen 2 top coordinate in pixels. ",
		.prop_name = WACOM_PROP_SCREENAREA,
		.prop_format = 32,
		.prop_offset = 9,
		.prop_flags = PROP_FLAG_READONLY
	},
	{
		.name = "SBottomX2",
		.desc = "Screen 2 right coordinate in pixels. ",
		.prop_name = WACOM_PROP_SCREENAREA,
		.prop_offset = 10,
		.prop_format = 32,
		.prop_flags = PROP_FLAG_READONLY
	},
	{
		.name = "SBottomY2",
		.desc = "Screen 2 bottom coordinate in pixels. ",
		.prop_name = WACOM_PROP_SCREENAREA,
		.prop_format = 32,
		.prop_offset = 11,
		.prop_flags = PROP_FLAG_READONLY
	},
	{
		.name = "STopX3",
		.desc = "Screen 3 left coordinate in pixels. ",
		.prop_name = WACOM_PROP_SCREENAREA,
		.prop_format = 32,
		.prop_offset = 12,
		.prop_flags = PROP_FLAG_READONLY
	},
	{
		.name = "STopY3",
		.desc = "Screen 3 top coordinate in pixels. ",
		.prop_name = WACOM_PROP_SCREENAREA,
		.prop_format = 32,
		.prop_offset = 13,
		.prop_flags = PROP_FLAG_READONLY
	},
	{
		.name = "SBottomX3",
		.desc = "Screen 3 right coordinate in pixels. ",
		.prop_name = WACOM_PROP_SCREENAREA,
		.prop_format = 32,
		.prop_offset = 14,
		.prop_flags = PROP_FLAG_READONLY
	},
	{
		.name = "SBottomY3",
		.desc = "Screen 3 bottom coordinate in pixels. ",
		.prop_name = WACOM_PROP_SCREENAREA,
		.prop_format = 32,
		.prop_offset = 15,
		.prop_flags = PROP_FLAG_READONLY
	},
	{
		.name = "STopX4",
		.desc = "Screen 4 left coordinate in pixels. ",
		.prop_name = WACOM_PROP_SCREENAREA,
		.prop_format = 32,
		.prop_offset = 16,
		.prop_flags = PROP_FLAG_READONLY
	},
	{
		.name = "STopY4",
		.desc = "Screen 4 top coordinate in pixels. ",
		.prop_name = WACOM_PROP_SCREENAREA,
		.prop_format = 32,
		.prop_offset = 17,
		.prop_flags = PROP_FLAG_READONLY
	},
	{
		.name = "SBottomX4",
		.desc = "Screen 4 right coordinate in pixels. ",
		.prop_name = WACOM_PROP_SCREENAREA,
		.prop_format = 32,
		.prop_offset = 18,
		.prop_flags = PROP_FLAG_READONLY
	},
	{
		.name = "SBottomY4",
		.desc = "Screen 4 bottom coordinate in pixels. ",
		.prop_name = WACOM_PROP_SCREENAREA,
		.prop_format = 32,
		.prop_offset = 19,
		.prop_flags = PROP_FLAG_READONLY
	},
	{
		.name = "STopX5",
		.desc = "Screen 5 left coordinate in pixels. ",
		.prop_name = WACOM_PROP_SCREENAREA,
		.prop_format = 32,
		.prop_offset = 20,
		.prop_flags = PROP_FLAG_READONLY
	},
	{
		.name = "STopY5",
		.desc = "Screen 5 top coordinate in pixels. ",
		.prop_name = WACOM_PROP_SCREENAREA,
		.prop_format = 32,
		.prop_offset = 21,
		.prop_flags = PROP_FLAG_READONLY
	},
	{
		.name = "SBottomX5",
		.desc = "Screen 5 right coordinate in pixels. ",
		.prop_name = WACOM_PROP_SCREENAREA,
		.prop_format = 32,
		.prop_offset = 22,
		.prop_flags = PROP_FLAG_READONLY
	},
	{
		.name = "SBottomY5",
		.desc = "Screen 5 bottom coordinate in pixels. ",
		.prop_name = WACOM_PROP_SCREENAREA,
		.prop_format = 32,
		.prop_offset = 23,
		.prop_flags = PROP_FLAG_READONLY
	},
	{
		.name = "STopX6",
		.desc = "Screen 6 left coordinate in pixels. ",
		.prop_name = WACOM_PROP_SCREENAREA,
		.prop_format = 32,
		.prop_offset = 24,
		.prop_flags = PROP_FLAG_READONLY
	},
	{
		.name = "STopY6",
		.desc = "Screen 6 top coordinate in pixels. ",
		.prop_name = WACOM_PROP_SCREENAREA,
		.prop_format = 32,
		.prop_offset = 25,
		.prop_flags = PROP_FLAG_READONLY
	},
	{
		.name = "SBottomX6",
		.desc = "Screen 6 right coordinate in pixels. ",
		.prop_name = WACOM_PROP_SCREENAREA,
		.prop_format = 32,
		.prop_offset = 26,
		.prop_flags = PROP_FLAG_READONLY
	},
	{
		.name = "SBottomY6",
		.desc = "Screen 6 bottom coordinate in pixels. ",
		.prop_name = WACOM_PROP_SCREENAREA,
		.prop_format = 32,
		.prop_offset = 27,
		.prop_flags = PROP_FLAG_READONLY
	},
	{
		.name = "STopX7",
		.desc = "Screen 7 left coordinate in pixels. ",
		.prop_name = WACOM_PROP_SCREENAREA,
		.prop_format = 32,
		.prop_offset = 28,
		.prop_flags = PROP_FLAG_READONLY
	},
	{
		.name = "STopY7",
		"Screen 7 top coordinate in pixels. ",
		.prop_name = WACOM_PROP_SCREENAREA,
		.prop_format = 32,
		.prop_offset = 29,
		.prop_flags = PROP_FLAG_READONLY
	},
	{
		.name = "SBottomX7",
		.desc = "Screen 7 right coordinate in pixels. ",
		.prop_name = WACOM_PROP_SCREENAREA,
		.prop_format = 32,
		.prop_offset = 30,
		.prop_flags = PROP_FLAG_READONLY
	},
	{
		.name = "SBottomY7",
		.desc = "Screen 7 bottom coordinate in pixels. ",
		.prop_name = WACOM_PROP_SCREENAREA,
		.prop_format = 32,
		.prop_offset = 31,
		.prop_flags = PROP_FLAG_READONLY
	},
	{
		.name = "ToolID",
		.desc = "Returns the ID of the associated device. ",
		.prop_name = WACOM_PROP_TOOL_TYPE,
		.prop_format = 32,
		.prop_offset = 0,
		.prop_flags = PROP_FLAG_READONLY
	},
	{
		.name = "ToolSerial",
		.desc = "Returns the serial number of the associated device. ",
		.prop_name = WACOM_PROP_SERIALIDS,
		.prop_format = 32,
		.prop_offset = 3,
		.prop_flags = PROP_FLAG_READONLY
	},
	{
		.name = "TabletID",
		.desc = "Returns the tablet ID of the associated device. ",
		.prop_name = WACOM_PROP_SERIALIDS,
		.prop_format = 32,
		.prop_offset = 0,
		.prop_flags = PROP_FLAG_READONLY
	},
	{
		.name = "GetTabletID",
		.desc = "Returns the tablet ID of the associated device. ",
		.prop_name = WACOM_PROP_SERIALIDS,
		.prop_format = 32,
		.prop_offset = 0,
		.prop_flags = PROP_FLAG_READONLY
	},
	{
		.name = "all",
		.desc = "Get value for all parameters.",
		.get_func = get_all,
		.prop_flags = PROP_FLAG_READONLY,
	},
	{ NULL }
};

struct modifier {
	char *name;
	char *converted;
};

static struct modifier modifiers[] = {
	{"ctrl", "Control_L"},
	{"ctl", "Control_L"},
	{"control", "Control_L"},
	{"lctrl", "Control_L"},
	{"rctrl", "Control_R"},

	{"meta", "Meta_L"},
	{"lmeta", "Meta_L"},
	{"rmeta", "Meta_R"},

	{"alt", "Alt_L"},
	{"lalt", "Alt_L"},
	{"ralt", "Alt_R"},

	{"shift", "Shift_L"},
	{"lshift", "Shift_L"},
	{"rshift", "Shift_R"},

	{ NULL, NULL }
};

static struct modifier specialkeys[] = {
	{"f1", "F1"}, {"f2", "F2"}, {"f3", "F3"},
	{"f4", "F4"}, {"f5", "F5"}, {"f6", "F6"},
	{"f7", "F7"}, {"f8", "F8"}, {"f9", "F9"},
	{"f10", "F10"}, {"f11", "F11"}, {"f12", "F12"},
	{"f13", "F13"}, {"f14", "F14"}, {"f15", "F15"},
	{"f16", "F16"}, {"f17", "F17"}, {"f18", "F18"},
	{"f19", "F19"}, {"f20", "F20"}, {"f21", "F21"},
	{"f22", "F22"}, {"f23", "F23"}, {"f24", "F24"},
	{"f25", "F25"}, {"f26", "F26"}, {"f27", "F27"},
	{"f28", "F28"}, {"f29", "F29"}, {"f30", "F30"},
	{"f31", "F31"}, {"f32", "F32"}, {"f33", "F33"},
	{"f34", "F34"}, {"f35", "F35"},

	{"esc", "Escape"}, {"Esc", "Escape"},

	{"up", "Up"}, {"down", "Down"},
	{"left", "Left"}, {"right", "Right"},

	{"backspace", "BackSpace"}, {"Backspace", "BackSpace"},

	{ NULL, NULL }
};

static param_t* find_parameter(char *name)
{
	param_t *param = NULL;

	for (param = parameters; param->name; param++)
		if (strcasecmp(name, param->name) == 0)
			break;
	return param->name ? param : NULL;
}

static void print_value(param_t *param, const char *msg, ...)
{
	va_list va_args;
	va_start(va_args, msg);
	switch(param->printformat)
	{
		case FORMAT_XORG_CONF:
			printf("Option \"%s\" \"", param->name);
			vprintf(msg, va_args);
			printf("\"\n");
			break;
		case FORMAT_SHELL:
			printf("xsetwacom set \"%s\" \"%s\" \"",
					param->device_name, param->name);
			vprintf(msg, va_args);
			printf("\"\n");
			break;
		default:
			vprintf(msg, va_args);
			printf("\n");
			break;
	}

	va_end(va_args);
}

static void usage(void)
{
	printf(
	"Usage: xsetwacom [options] [command [arguments...]]\n"
	"Options:\n"
	" -h, --help                 - usage\n"
	" -v, --verbose              - verbose output\n"
	" -V, --version              - version info\n"
	" -d, --display disp_name    - override default display\n"
	" -s, --shell                - generate shell commands for 'get'\n"
	" -x, --xconf                - generate X.conf lines for 'get'\n");

	printf(
	"\nCommands:\n"
	" --list [dev|param]           - display known devices, parameters \n"
	" --list mod                   - display supported modifier and specific keys for keystrokes\n"
	" --set dev_name param [values...] - set device parameter by name\n"
	" --get dev_name param [param...] - get current device parameter(s) value by name\n");
}


static void version(void)
{
	printf("%d.%d.%d\n", PACKAGE_VERSION_MAJOR, PACKAGE_VERSION_MINOR,
			     PACKAGE_VERSION_PATCHLEVEL);
}

static XDevice* find_device(Display *display, char *name)
{
	XDeviceInfo	*devices;
	XDeviceInfo	*found = NULL;
	XDevice		*dev = NULL;
	int		i, num_devices;
	int		len = strlen(name);
	Bool		is_id = True;
	XID		id = -1;

	for(i = 0; i < len; i++)
	{
		if (!isdigit(name[i]))
		{
			is_id = False;
			break;
		}
	}

	if (is_id)
		id = atoi(name);

	devices = XListInputDevices(display, &num_devices);

	for(i = 0; i < num_devices; i++)
	{
		TRACE("Checking device '%s' (%ld).\n", devices[i].name, devices[i].id);

		if (((devices[i].use >= IsXExtensionDevice)) &&
			((!is_id && strcmp(devices[i].name, name) == 0) ||
			 (is_id && devices[i].id == id)))
		{
			if (found) {
				fprintf(stderr, "Warning: There are multiple devices named \"%s\".\n"
						"To ensure the correct one is selected, please use "
						"the device ID instead.\n\n", name);
				found = NULL;
				break;
			} else {
				found = &devices[i];
			}
		}
	}

	if (found)
	{
		TRACE("Device '%s' (%ld) found.\n", found->name, found->id);
		dev = XOpenDevice(display, found->id);
	}

	XFreeDeviceList(devices);

	return dev;
}

/* Return True if the given device has the property, or False otherwise */
static Bool test_property(Display *dpy, XDevice* dev, Atom prop)
{
	int nprops_return;
	Atom *properties;
	int found = False;

	/* if no property is required, return success */
	if (prop == None)
		return True;

	properties = XListDeviceProperties(dpy, dev, &nprops_return);

	while(nprops_return--)
	{
		if (properties[nprops_return] == prop)
		{
			found = True;
			break;
		}
	}

	XFree(properties);
	return found;
}

static void list_one_device(Display *dpy, XDeviceInfo *info)
{
	static int	wacom_prop = 0;
	int		natoms;
	Atom		*atoms;
	XDevice		*dev;
	char		*type_name = NULL;

	if (!wacom_prop)
		wacom_prop = XInternAtom(dpy, "Wacom Tool Type", True);

	dev = XOpenDevice(dpy, info->id);
	if (!dev)
		return;

	atoms = XListDeviceProperties(dpy, dev, &natoms);
	if (natoms)
	{
		int j;
		for (j = 0; j < natoms; j++)
			if (atoms[j] == wacom_prop)
				break;

		if (j <= natoms)
		{
			unsigned char	*data;
			Atom		type;
			int		format;
			unsigned long	nitems, bytes_after;

			XGetDeviceProperty(dpy, dev, wacom_prop, 0, 1,
					   False, AnyPropertyType, &type,
					   &format, &nitems, &bytes_after,
					   &data);
			if (nitems)
			{
				type_name = XGetAtomName(dpy, *(Atom*)data);
				printf("%-16s %-10s\n", info->name, type_name);
			}

			XFree(data);
		} else {
			TRACE("'%s' (%ld) is not a wacom device.\n", info->name, info->id);
		}

		XFree(atoms);
	}

	XCloseDevice(dpy, dev);
	XFree(type_name);
}

static void list_devices(Display *dpy)
{
	XDeviceInfo	*info;
	int		ndevices, i;
	Atom		wacom_prop;


	wacom_prop = XInternAtom(dpy, "Wacom Tool Type", True);
	if (wacom_prop == None)
		return;

	info = XListInputDevices(dpy, &ndevices);

	for (i = 0; i < ndevices; i++)
	{
		if (info[i].use == IsXPointer || info[i].use == IsXKeyboard)
			continue;

		TRACE("Found device '%s' (%ld).\n", info[i].name, info[i].id);
		list_one_device(dpy, &info[i]);
	}

	XFreeDeviceList(info);
}


static void list_param(Display *dpy)
{
	param_t *param = parameters;

	while(param->name)
	{
		printf("%-16s - %16s\n", param->name, param->desc);
		param++;
	}
}

static void list_mod(Display *dpy)
{
	struct modifier *m = modifiers;

	printf("%d modifiers are supported:\n", ArrayLength(modifiers) - 1);
	while(m->name)
		printf("	%s\n", m++->name);

	printf("\n%d specialkeys are supported:\n", ArrayLength(specialkeys) - 1);
	m = specialkeys;
	while(m->name)
		printf("	%s\n", m++->name);
}

static void list(Display *dpy, int argc, char **argv)
{
	TRACE("'list' requested.\n");
	if (argc == 0)
		list_devices(dpy);
	else if (strcmp(argv[0], "dev") == 0)
		list_devices(dpy);
	else if (strcmp(argv[0], "param") == 0)
		list_param(dpy);
	else if (strcmp(argv[0], "mod") == 0)
		list_mod(dpy);
	else
		printf("unknown argument to list.\n");
}
/*
 * Convert a list of random special keys to strings that can be passed into
 * XStringToKeysym
 */
static char *convert_specialkey(const char *modifier)
{
	struct modifier *m = modifiers;

	while(m->name && strcasecmp(modifier, m->name))
		m++;

	if (!m->name)
	{
		m = specialkeys;
		while(m->name && strcasecmp(modifier, m->name))
			m++;
	}

	return m->converted ? m->converted : (char*)modifier;
}

static int is_modifier(const char* modifier)
{
	const char *modifiers[] = {
		"Control_L",
		"Control_R",
		"Alt_L",
		"Alt_R",
		"Shift_L",
		"Shift_R",
		"Meta_L",
		"Meta_R",
		NULL,
	};

	const char **m = modifiers;

	while(*m)
	{
		if (strcmp(modifier, *m) == 0)
			return 1;
		m++;
	}

	return 0;
}

static int special_map_keystrokes(Display *dpy, int argc, char **argv, unsigned long *ndata, unsigned long* data);
static int special_map_button(Display *dpy, int argc, char **argv, unsigned long *ndata, unsigned long* data);
static int special_map_core(Display *dpy, int argc, char **argv, unsigned long *ndata, unsigned long *data);
static int special_map_modetoggle(Display *dpy, int argc, char **argv, unsigned long *ndata, unsigned long *data);
static int special_map_displaytoggle(Display *dpy, int argc, char **argv, unsigned long *ndata, unsigned long *data);

/* Valid keywords for the --set ButtonX options */
struct keywords {
	const char *keyword;
	int (*func)(Display*, int, char **, unsigned long*, unsigned long *);
} keywords[] = {
	{"key", special_map_keystrokes},
	{"button", special_map_button},
	{"core", special_map_core},
	{"modetoggle", special_map_modetoggle},
	{"displaytoggle", special_map_displaytoggle},
	{ NULL, NULL }
};

/* the "core" keyword isn't supported anymore, we just have this here to
   tell people that. */
static int special_map_core(Display *dpy, int argc, char **argv, unsigned long *ndata, unsigned long *data)
{
	static int once_only = 1;
	if (once_only)
	{
		printf ("Note: The \"core\" keyword is not supported anymore and "
			"will be ignored.\n");
		once_only = 0;
	}
	return 0;
}

static int special_map_modetoggle(Display *dpy, int argc, char **argv, unsigned long *ndata, unsigned long *data)
{
	data[*ndata] = AC_MODETOGGLE;

	*ndata += 1;

	return 0;
}

static int special_map_displaytoggle(Display *dpy, int argc, char **argv, unsigned long *ndata, unsigned long *data)
{
	data[*ndata] = AC_DISPLAYTOGGLE;

	*ndata += 1;

	return 0;
}

static inline int is_valid_keyword(const char *keyword)
{
	struct keywords *kw = keywords;

	while(kw->keyword)
	{
		if (strcmp(keyword, kw->keyword) == 0)
			return 1;
		kw++;
	}
	return 0;
}

static int special_map_button(Display *dpy, int argc, char **argv, unsigned long *ndata, unsigned long *data)
{
	int nitems = 0;
	int i;

	for (i = 0; i < argc; i++)
	{
		char *btn = argv[i];
		int button;
		int need_press = 0, need_release = 0;

		if (strlen(btn) > 1)
		{
			if (is_valid_keyword(btn))
				break;

			switch (btn[0])
			{
				case '+': need_press = 1; break;
				case '-': need_release= 1; break;
				default:
					  need_press = need_release = 1;
					  break;
			}
		} else
			need_press = need_release = 1;

		if (sscanf(btn, "%d", &button) != 1)
			return nitems;


		TRACE("Button map %d [%s,%s]\n", abs(button),
				need_press ?  "press" : "",
				need_release ?  "release" : "");

		if (need_press)
			data[*ndata + nitems++] = AC_BUTTON | AC_KEYBTNPRESS | abs(button);
		if (need_release)
			data[*ndata + nitems++] = AC_BUTTON | abs(button);
	}

	*ndata += nitems;
	return nitems;
}

/* Return the first keycode to have the required keysym in the current group.
   TODOs:
   - parse other groups as well (do we need this?)
   - for keysyms not on level 0, return the keycodes for the modifiers as
     well
*/
static int keysym_to_keycode(Display *dpy, KeySym sym)
{
	static XkbDescPtr xkb = NULL;
	XkbStateRec state;
	int group;
	int kc = 0;


	if (!xkb)
		xkb = XkbGetKeyboard(dpy, XkbAllComponentsMask, XkbUseCoreKbd);
	XkbGetState(dpy, XkbUseCoreKbd, &state);
	group = state.group;

	for (kc = xkb->min_key_code; kc <= xkb->max_key_code; kc++)
	{
		KeySym* ks;
		int i;

		ks = XkbKeySymsPtr(xkb, kc);
		for (i = 0; i < XkbKeyGroupWidth(xkb, kc, state.group); i++)
			if (ks[i] == sym)
				goto out;
	}

out:
	return kc;
}
/*
   Map gibberish like "ctrl alt f2" into the matching AC_KEY values.
   Returns 1 on success or 0 otherwise.
 */
static int special_map_keystrokes(Display *dpy, int argc, char **argv, unsigned long *ndata, unsigned long* data)
{
	int i;
	int nitems = 0;

	for (i = 0; i < argc; i++)
	{
		KeySym ks;
		KeyCode kc;
		int need_press = 0, need_release = 0;
		char *key = argv[i];

		if (strlen(key) > 1)
		{
			if (is_valid_keyword(key))
				break;

			switch(key[0])
			{
				case '+':
					need_press = 1;
					key++;
					break;
				case '-':
					need_release = 1;
					key++;
					break;
				default:
					need_press = need_release = 1;
					break;
			}

			/* Function keys must be uppercased */
			if (strlen(key) > 1)
				key = convert_specialkey(key);

			if (!key || !XStringToKeysym(key))
			{
				fprintf(stderr, "Invalid key '%s'.\n", argv[i]);
				break;
			}

			if (is_modifier(key) && (need_press && need_release))
				need_release = 0;

		} else
			need_press = need_release = 1;

		ks = XStringToKeysym(key);
		kc = keysym_to_keycode(dpy, ks);

		if (need_press)
			data[*ndata + nitems++] = AC_KEY | AC_KEYBTNPRESS | kc;
		if (need_release)
			data[*ndata + nitems++] = AC_KEY | kc;

		TRACE("Key map %ld (%d, '%s') [%s,%s]\n", ks, kc,
				XKeysymToString(ks),
				need_press ?  "press" : "",
				need_release ?  "release" : "");

	}

	*ndata += nitems;
	return i;
}

/* Join a bunch of argv into a string, then split up again at the spaces
 * into words. Returns a char** array sized *nwords, each element pointing
 * to s strdup'd string.
 * Memory to be freed by the caller.
 */
static char** strjoinsplit(int argc, char **argv, int *nwords)
{
	char buff[1024] = { 0 };
	char **words	= NULL;
	char *tmp, *tok;

	while(argc--)
	{
		if (strlen(buff) + strlen(*argv) + 1 >= sizeof(buff))
			break;

		strcat(buff, *argv);
		strcat(buff, " ");
		argv++;
	}

	*nwords = 0;

	for (tmp = buff; tmp && *tmp != '\0'; tmp = index((const char*)tmp, ' ') + 1)
		(*nwords)++;

	words = calloc(*nwords, sizeof(char*));

	*nwords = 0;
	tok = strtok(buff, " ");
	while(tok)
	{
		words[(*nwords)++] = strdup(tok);
		tok = strtok(NULL, " ");
	}

	return words;
}

static int get_button_number_from_string(const char* string)
{
	int slen = strlen("Button");
	if (slen >= strlen(string) || strncasecmp(string, "Button", slen))
		return -1;
	return atoi(&string[strlen("Button")]);
}

/* Handles complex button mappings through button actions. */
static void special_map_buttons(Display *dpy, XDevice *dev, param_t* param, int argc, char **argv)
{
	Atom btnact_prop, prop;
	unsigned long *data, *btnact_data;
	int slen = strlen("Button");
	int btn_no;
	Atom type;
	int format;
	unsigned long btnact_nitems, nitems, bytes_after;
	int need_update = 0;
	int i;
	int nwords = 0;
	char **words = NULL;

	TRACE("Special %s map for device %ld.\n", param->name, dev->device_id);

	if (slen >= strlen(param->name) || strncmp(param->name, "Button", slen))
		return;

	btnact_prop = XInternAtom(dpy, "Wacom Button Actions", True);
	if (!btnact_prop)
		return;

	btn_no = get_button_number_from_string(param->name);
	btn_no--; /* property is zero-indexed, button numbers are 1-indexed */

	XGetDeviceProperty(dpy, dev, btnact_prop, 0, 100, False,
				AnyPropertyType, &type, &format, &btnact_nitems,
				&bytes_after, (unsigned char**)&btnact_data);

	if (btn_no > btnact_nitems)
		return;

	/* some atom already assigned, modify that */
	if (btnact_data[btn_no])
		prop = btnact_data[btn_no];
	else
	{
		char buff[64];
		sprintf(buff, "Wacom button action %d", (btn_no + 1));
		prop = XInternAtom(dpy, buff, False);

		btnact_data[btn_no] = prop;
		need_update = 1;
	}

	data = calloc(sizeof(long), 256);
	nitems = 0;

	/* translate cmdline commands */
	words = strjoinsplit(argc, argv, &nwords);
	for (i = 0; i < nwords; i++)
	{
		int j = 0;
		while (keywords[j].keyword && i < nwords)
		{
			int parsed = 0;
			if (strcasecmp(words[i], keywords[j].keyword) == 0)
			{
				parsed = keywords[j].func(dpy, nwords - i - 1,
							  &words[i + 1],
							  &nitems, data);
				i += parsed;
			}
			if (parsed)
				j = parsed = 0; /* restart with first keyword */
			else
				j++;
		}
	}

	XChangeDeviceProperty(dpy, dev, prop, XA_INTEGER, 32,
				PropModeReplace,
				(unsigned char*)data, nitems);

	if (need_update)
		XChangeDeviceProperty(dpy, dev, btnact_prop, XA_ATOM, 32,
					PropModeReplace,
					(unsigned char*)btnact_data,
					btnact_nitems);
	XFlush(dpy);
}


static void map_button_simple(Display *dpy, XDevice *dev, param_t* param, int button)
{
	int nmap = 256;
	unsigned char map[nmap];
	int btn_no = 0;

	btn_no = get_button_number_from_string(param->name);
	if (btn_no == -1)
		return;

	nmap = XGetDeviceButtonMapping(dpy, dev, map, nmap);
	if (btn_no >= nmap)
	{
		fprintf(stderr, "Button number does not exist on device.\n");
		return;
	}

	map[btn_no - 1] = button;
	XSetDeviceButtonMapping(dpy, dev, map, nmap);
	XFlush(dpy);
}
/*
   Supports three variations.
   xsetwacom set device Button1 1
	- maps button 1 to logical button 1
   xsetwacom set device Button1 "key a b c d"
	- maps button 1 to key events a b c d
 */
static void map_button(Display *dpy, XDevice *dev, param_t* param, int argc, char **argv)
{
	int button;

	if (argc <= 0)
		return;

	TRACE("Mapping %s for device %ld.\n", param->name, dev->device_id);

	/* --set "device" Button1 3 */
	if (sscanf(argv[0], "%d", &button) == 1)
		map_button_simple(dpy, dev, param, button);
	else
		special_map_buttons(dpy, dev, param, argc, argv);
}

static void set_xydefault(Display *dpy, XDevice *dev, param_t* param, int argc, char **argv)
{
	Atom prop, type;
	int format;
	unsigned char* data = NULL;
	unsigned long nitems, bytes_after;
	long *ldata;

	prop = XInternAtom(dpy, param->prop_name, True);
	if (!prop)
	{
		fprintf(stderr, "Property for '%s' not available.\n",
			param->name);
		goto out;
	}

	XGetDeviceProperty(dpy, dev, prop, 0, 1000, False, AnyPropertyType,
				&type, &format, &nitems, &bytes_after, &data);

	if (nitems <= param->prop_offset)
	{
		fprintf(stderr, "Property offset doesn't exist, this is a bug.\n");
		goto out;
	}

	ldata = (long*)data;
	ldata[0] = -1;
	ldata[1] = -1;
	ldata[2] = -1;
	ldata[3] = -1;

	XChangeDeviceProperty(dpy, dev, prop, type, format,
				PropModeReplace, data, nitems);
	XFlush(dpy);
out:
	free(data);
}

static void set_mode(Display *dpy, XDevice *dev, param_t* param, int argc, char **argv)
{
	int mode = Absolute;
	if (argc < 1)
	{
		usage();
		return;
	}

	TRACE("Set mode '%s' for device %ld.\n", argv[0], dev->device_id);

	if (strcasecmp(argv[0], "Relative") == 0)
		mode = Relative;
	else if (strcasecmp(argv[0], "Absolute") == 0)
		mode = Absolute;
	else
	{
		printf("Invalid device mode. Use 'Relative' or 'Absolute'.\n");
		return;
	}


	XSetDeviceMode(dpy, dev, mode);
	XFlush(dpy);
}

static void set_rotate(Display *dpy, XDevice *dev, param_t* param, int argc, char **argv)
{
	int rotation = 0;
	Atom prop, type;
	int format;
	unsigned char* data;
	unsigned long nitems, bytes_after;

	if (argc != 1)
		goto error;

	TRACE("Rotate '%s' for device %ld.\n", argv[0], dev->device_id);

	if (strcasecmp(argv[0], "CW") == 0)
		rotation = 1;
	else if (strcasecmp(argv[0], "CCW") == 0)
		rotation = 2;
	else if (strcasecmp(argv[0], "HALF") == 0)
		rotation = 3;
	else if (strcasecmp(argv[0], "NONE") == 0)
		rotation = 0;
	else if (strlen(argv[0]) == 1)
	{
		rotation = atoi(argv[0]);
		if (rotation < 0 || rotation > 3)
			goto error;
	}

	prop = XInternAtom(dpy, param->prop_name, True);
	if (!prop)
	{
		fprintf(stderr, "Property for '%s' not available.\n",
			param->name);
		return;
	}

	XGetDeviceProperty(dpy, dev, prop, 0, 1000, False, AnyPropertyType,
				&type, &format, &nitems, &bytes_after, &data);

	if (nitems == 0 || format != 8)
	{
		fprintf(stderr, "Property for '%s' has no or wrong value - this is a bug.\n",
			param->name);
		return;
	}

	*data = rotation;
	XChangeDeviceProperty(dpy, dev, prop, type, format,
				PropModeReplace, data, nitems);
	XFlush(dpy);

	return;

error:
	fprintf(stderr, "Usage: xsetwacom <device name> Rotate [NONE | CW | CCW | HALF]\n");
	return;
}

static void set_twinview(Display *dpy, XDevice *dev, param_t* param, int argc, char **argv)
{
	int twinview = 0;
	Atom prop, type;
	int format;
	unsigned char* data;
	unsigned long nitems, bytes_after;

	if (argc != 1)
		goto error;

	TRACE("TwinView '%s' for device %ld.\n", argv[0], dev->device_id);

	if (strcasecmp(argv[0], "none") == 0)
		twinview = TV_NONE;
	else if (strcasecmp(argv[0], "horizontal") == 0)
		twinview = TV_LEFT_RIGHT;
	else if (strcasecmp(argv[0], "vertical") == 0)
		twinview = TV_ABOVE_BELOW;
	else
		goto error;

	prop = XInternAtom(dpy, param->prop_name, True);
	if (!prop)
	{
		fprintf(stderr, "Property for '%s' not available.\n",
			param->name);
		return;
	}

	XGetDeviceProperty(dpy, dev, prop, 0, 1000, False, AnyPropertyType,
				&type, &format, &nitems, &bytes_after, &data);

	if (nitems == 0 || format != 8)
	{
		fprintf(stderr, "Property for '%s' has no or wrong value - this is a bug.\n",
			param->name);
		return;
	}

	data[param->prop_offset] = twinview;
	XChangeDeviceProperty(dpy, dev, prop, type, format,
				PropModeReplace, data, nitems);
	XFlush(dpy);

	return;

error:
	fprintf(stderr, "Usage: xsetwacom rotate <device name> [NONE | CW | CCW | HALF]\n");
	return;
}

static int convert_value_from_user(param_t *param, char *value)
{
	int val;

	if ((param->prop_flags & PROP_FLAG_BOOLEAN) && strcmp(value, "off") == 0)
			val = 0;
	else if ((param->prop_flags & PROP_FLAG_BOOLEAN) && strcmp(value, "on") == 0)
			val = 1;
	else
		val = atoi(value);

	return val;
}

static void set(Display *dpy, int argc, char **argv)
{
	param_t *param;
	XDevice *dev = NULL;
	Atom prop = None, type;
	int format;
	unsigned char* data = NULL;
	unsigned long nitems, bytes_after;
	double val;
	long *n;
	char *b;
	int i;
	char **values;
	int nvals;

	if (argc < 3)
	{
		usage();
		return;
	}

	TRACE("'set' requested for '%s'.\n", argv[0]);

	dev = find_device(dpy, argv[0]);
	if (!dev)
	{
		printf("Cannot find device '%s'.\n", argv[0]);
		return;
	}

	param = find_parameter(argv[1]);
	if (!param)
	{
		printf("Unknown parameter name '%s'.\n", argv[1]);
		goto out;
	} else if (param->prop_flags & PROP_FLAG_READONLY)
	{
		printf("'%s' is a read-only option.\n", argv[1]);
		goto out;
	}

	if (param->prop_name)
	{
		prop = XInternAtom(dpy, param->prop_name, True);
		if (!prop || !test_property(dpy, dev, prop))
		{
			printf("Property '%s' does not exist on device.\n",
				param->prop_name);
			goto out;
		}
	}

	if (param->set_func)
	{
		param->set_func(dpy, dev, param, argc - 2, &argv[2]);
		goto out;
	}

	XGetDeviceProperty(dpy, dev, prop, 0, 1000, False, AnyPropertyType,
				&type, &format, &nitems, &bytes_after, &data);

	if (nitems <= param->prop_offset)
	{
		fprintf(stderr, "Property offset doesn't exist.\n");
		goto out;
	}

	values = strjoinsplit(argc - 2, &argv[2], &nvals);

	for (i = 0; i < nvals; i++)
	{
		val = convert_value_from_user(param, values[i]);

		switch(param->prop_format)
		{
			case 8:
				if (format != param->prop_format || type != XA_INTEGER) {
					fprintf(stderr, "   %-23s = format mismatch (%d)\n",
							param->name, format);
					break;
				}
				b = (char*)data;
				b[param->prop_offset + i] = rint(val);
				break;
			case 32:
				if (format != param->prop_format || type != XA_INTEGER) {
					fprintf(stderr, "   %-23s = format mismatch (%d)\n",
							param->name, format);
					break;
				}
				n = (long*)data;
				n[param->prop_offset + i] = rint(val);
				break;
		}
	}

	XChangeDeviceProperty(dpy, dev, prop, type, format,
				PropModeReplace, data, nitems);
	XFlush(dpy);

	for (i = 0; i < nvals; i++)
		free(values[i]);
	free(values);
out:
	XCloseDevice(dpy, dev);
	free(data);
}

static void get_mode(Display *dpy, XDevice *dev, param_t* param, int argc, char **argv)
{
	XDeviceInfo *info, *d = NULL;
	int ndevices, i;
	XValuatorInfoPtr v;

	info = XListInputDevices(dpy, &ndevices);
	while(ndevices--)
	{
		d = &info[ndevices];
		if (d->id == dev->device_id)
			break;
	}

	if (!ndevices) /* device id 0 is reserved and can't be our device */
		return;

	TRACE("Getting mode for device %ld.\n", dev->device_id);

	v = (XValuatorInfoPtr)d->inputclassinfo;
	for (i = 0; i < d->num_classes; i++)
	{
		if (v->class == ValuatorClass)
		{
			print_value(param, "%s", (v->mode == Absolute) ? "Absolute" : "Relative");
			break;
		}
		v = (XValuatorInfoPtr)((char*)v + v->length);
	}

	XFreeDeviceList(info);
}

static void get_rotate(Display *dpy, XDevice *dev, param_t* param, int argc, char **argv)
{
	char *rotation = NULL;
	Atom prop, type;
	int format;
	unsigned char* data;
	unsigned long nitems, bytes_after;

	prop = XInternAtom(dpy, param->prop_name, True);
	if (!prop)
	{
		fprintf(stderr, "Property for '%s' not available.\n",
			param->name);
		return;
	}

	TRACE("Getting rotation for device %ld.\n", dev->device_id);

	XGetDeviceProperty(dpy, dev, prop, 0, 1000, False, AnyPropertyType,
				&type, &format, &nitems, &bytes_after, &data);

	if (nitems == 0 || format != 8)
	{
		fprintf(stderr, "Property for '%s' has no or wrong value - this is a bug.\n",
			param->name);
		return;
	}

	switch(*data)
	{
		case 0:
			rotation = "NONE";
			break;
		case 1:
			rotation = "CW";
			break;
		case 2:
			rotation = "CCW";
			break;
		case 3:
			rotation = "HALF";
			break;
	}

	print_value(param, "%s", rotation);

	return;
}

static void get_twinview(Display *dpy, XDevice *dev, param_t *param, int argc, char **argv)
{
	char *twinview = NULL;
	Atom prop, type;
	int format;
	unsigned char* data;
	unsigned long nitems, bytes_after;

	prop = XInternAtom(dpy, param->prop_name, True);
	if (!prop)
	{
		fprintf(stderr, "Property for '%s' not available.\n",
			param->name);
		return;
	}

	TRACE("Getting twinview setting for device %ld.\n", dev->device_id);

	XGetDeviceProperty(dpy, dev, prop, 0, 1000, False, AnyPropertyType,
				&type, &format, &nitems, &bytes_after, &data);

	if (nitems == 0 || format != 8)
	{
		fprintf(stderr, "Property for '%s' has no or wrong value - this is a bug.\n",
			param->name);
		return;
	}

	switch(data[param->prop_offset])
	{
		case TV_NONE: twinview = "none"; break;
		case TV_ABOVE_BELOW: twinview = "vertical"; break;
		case TV_LEFT_RIGHT: twinview = "horizontal"; break;
		default:
				    break;
	}

	print_value(param, "%s", twinview);

	return;
}

static void get_presscurve(Display *dpy, XDevice *dev, param_t *param, int argc,
				char **argv)
{
	Atom prop, type;
	int format, i;
	unsigned char* data;
	unsigned long nitems, bytes_after;
	char buff[256] = {0};
	long *ldata;

	prop = XInternAtom(dpy, param->prop_name, True);
	if (!prop)
	{
		fprintf(stderr, "Property for '%s' not available.\n",
			param->name);
		return;
	}

	TRACE("Getting pressure curve for device %ld.\n", dev->device_id);

	XGetDeviceProperty(dpy, dev, prop, 0, 1000, False, AnyPropertyType,
				&type, &format, &nitems, &bytes_after, &data);

	if (param->prop_format != 32)
		return;

	ldata = (long*)data;
	if (nitems)
		sprintf(buff, "%ld", ldata[param->prop_offset]);
	for (i = 1; i < nitems; i++)
		sprintf(&buff[strlen(buff)], " %ld", ldata[param->prop_offset + i]);

	print_value(param, "%s", buff);
}

static void get_button(Display *dpy, XDevice *dev, param_t *param, int argc,
			char **argv)
{
	int nmap = 256;
	unsigned char map[nmap];
	int btn_no = 0;

	btn_no = get_button_number_from_string(param->name);
	if (btn_no == -1)
		return;

	TRACE("Getting button map curve for device %ld.\n", dev->device_id);

	nmap = XGetDeviceButtonMapping(dpy, dev, map, nmap);

	if (btn_no > nmap)
	{
		fprintf(stderr, "Button number does not exist on device.\n");
		return;
	}

	print_value(param, "%d", map[btn_no - 1]);

	XSetDeviceButtonMapping(dpy, dev, map, nmap);
	XFlush(dpy);
}

static void get_all(Display *dpy, XDevice *dev, param_t *param, int argc, char **argv)
{
	param_t *p = parameters;

	while(p->name)
	{
		if (p != param)
		{
			p->device_name = param->device_name;
			p->printformat = param->printformat;
			get_param(dpy, dev, p, argc, argv);
		}
		p++;
	}
}

static void get(Display *dpy, enum printformat printformat, int argc, char **argv)
{
	param_t *param;
	XDevice *dev = NULL;

	TRACE("'get' requested for '%s'.\n", argv[0]);

	if (argc < 2)
	{
		usage();
		return;
	}

	dev = find_device(dpy, argv[0]);
	if (!dev)
	{
		printf("Cannot find device '%s'.\n", argv[0]);
		return;
	}

	param = find_parameter(argv[1]);
	if (!param)
	{
		printf("Unknown parameter name '%s'.\n", argv[1]);
		return;
	} else if (param->prop_flags & PROP_FLAG_WRITEONLY)
	{
		printf("'%s' is a write-only option.\n", argv[1]);
		return;
	} else
	{
		param->printformat = printformat;
		param->device_name = argv[0];
	}

	get_param(dpy, dev, param, argc - 2, &argv[2]);

	XCloseDevice(dpy, dev);
}

static void get_param(Display *dpy, XDevice *dev, param_t *param, int argc, char **argv)
{
	Atom prop = None, type;
	int format;
	unsigned char* data;
	unsigned long nitems, bytes_after;

	if (param->prop_name)
	{
		prop = XInternAtom(dpy, param->prop_name, True);
		if (!prop || !test_property(dpy, dev, prop))
		{
			printf("Property '%s' does not exist on device.\n",
				param->prop_name);
			return;
		}
	}

	if (param->get_func)
	{
		param->get_func(dpy, dev, param, argc, argv);
		return;
	}

	XGetDeviceProperty(dpy, dev, prop, 0, 1000, False, AnyPropertyType,
				&type, &format, &nitems, &bytes_after, &data);

	if (nitems <= param->prop_offset)
	{
		fprintf(stderr, "Property offset doesn't exist.\n");
		return;
	}


	switch(param->prop_format)
	{
		case 8:
			{
				char str[10] = {0};
				int val = data[param->prop_offset];

				if (param->prop_flags & PROP_FLAG_BOOLEAN)
					sprintf(str, "%s", val ?  "on" : "off");
				else
					sprintf(str, "%d", val);
				print_value(param, "%s", str);
			}
			break;
		case 32:
			{
				long *ldata = (long*)data;
				print_value(param, "%ld", ldata[param->prop_offset]);
				break;
			}
	}
}


int main (int argc, char **argv)
{
	int c;
	int optidx;
	char *display = NULL;
	Display *dpy;
	int do_list = 0, do_set = 0, do_get = 0;
	enum printformat format = FORMAT_DEFAULT;

	struct option options[] = {
		{"help", 0, NULL, 0},
		{"verbose", 0, NULL, 0},
		{"version", 0, NULL, 0},
		{"display", 1, NULL, 'd'},
		{"shell", 0, NULL, 0},
		{"xconf", 0, NULL, 0},
		{"list", 0, NULL, 0},
		{"set", 0, NULL, 0},
		{"get", 0, NULL, 0},
		{NULL, 0, NULL, 0}
	};

	if (argc < 2)
	{
		usage();
		return 1;
	}

	while ((c = getopt_long(argc, argv, "+hvVd:sx", options, &optidx)) != -1) {
		switch(c)
		{
			case 0:
				switch(optidx)
				{
					case 0: usage(); break;
					case 1: verbose = True; break;
					case 2: version(); break;
					case 3: /* display */
						break;
					case 4:
						format = FORMAT_SHELL;
						break;
					case 5:
						format = FORMAT_XORG_CONF;
						break;
					case 6: do_list = 1; break;
					case 7: do_set = 1; break;
					case 8: do_get = 1; break;
				}
				break;
			case 'd':
				display = optarg;
				break;
			case 's':
				format = FORMAT_SHELL;
				break;
			case 'x':
				format = FORMAT_XORG_CONF;
				break;
			case 'v':
				verbose = True;
				break;
			case 'V':
				version();
				break;
			case 'h':
			default:
				usage();
				return 0;
		}
	}

	TRACE("Display is '%s'.\n", display);

	dpy = XOpenDisplay(display);
	if (!dpy)
	{
		printf("Failed to open Display %s.\n", display ? display : "");
		return -1;
	}

	if (!do_list && !do_get && !do_set)
	{
		if (optind < argc)
		{
			if (strcmp(argv[optind], "list") == 0)
			{
				do_list = 1;
				optind++;
			} else if (strcmp(argv[optind], "set") == 0)
			{
				do_set = 1;
				optind++;
			} else if (strcmp(argv[optind], "get") == 0)
			{
				do_get = 1;
				optind++;
			}
			else
				usage();
		} else
			usage();
	}

	if (do_list)
		list(dpy, argc - optind, &argv[optind]);
	else if (do_set)
		set(dpy, argc - optind, &argv[optind]);
	else if (do_get)
		get(dpy, format, argc - optind, &argv[optind]);

	XCloseDisplay(dpy);
	return 0;
}


/* vim: set noexpandtab shiftwidth=8: */
```

---

### Post by Favux on 2010-08-08
Oops!  My fault I was messing with xsetwacom.c earlier so it was on my brain.  I meant go to the /src directory in xf86-input-wacom and then open wcmCommon.c.  Sorry.

---

### Post by TheNerdAL on 2010-08-08
YES! It worked! Thank you so much! Do the gestures and zooming work too under Linux? 

I also want to know if it's possible to use the pen to draw and not accidentally draw using your hand.

EDIT: Oops, I accidentally tried the zooming gesture like in those Apple commercials and it made the words in Firefox bigger. :D It works!

---

### Post by Favux on 2010-08-08
Hi TheNerdAL,

Yes, as you discovered the gestures work.
> I also want to know if it's possible to use the pen to draw and not accidentally draw using your hand.
The pen should automatically shut off touch when it gets close to the tablet.  But if it isn't working right in some program that's what the touch toggle script in V. is for.

---

### Post by TheNerdAL on 2010-08-08
> **Favux said:**
> Hi TheNerdAL,

Yes, as you discovered the gestures work.

The pen should automatically shut off touch when it gets close to the tablet.  But if it isn't working right in some program that's what the touch toggle script in V. is for.

Got it, I'll try that. Also, how do I get the Eraser to work?

EDIT: And do I untar the file or just rename it?

---

### Post by cariboo on 2010-08-08
This has turned into a support thread, moved to General Help.

---

### Post by TheNerdAL on 2010-08-08
> **cariboo907 said:**
> This has turned into a support thread, moved to General Help.

You didn't move it. :P

---

### Post by Favux on 2010-08-08
Don't taunt the moderators!

Well you have to untar it first (right click and Extract here).  Then use the wacom.conf version and rename it and make it executable, ie follow the directions.  Remember to use the "Device names" for your tablet from 'xinput --list".

---

### Post by TheNerdAL on 2010-08-08
> **Favux said:**
> Don't taunt the moderators!

Well you have to untar it first (right click and Extract here).  Then use the wacom.conf version and rename it and make it executable, ie follow the directions.  Remember to use the "Device names" for your tablet from 'xinput --list".

That seems to work. :D Lol, now my last question. How do I get my mouse to erase?

---

### Post by Favux on 2010-08-08
> How do I get my mouse to erase? 
I'm hoping you mean the eraser on the stylus.  If you look near the bottom of the [Wacom wiki]("https://help.ubuntu.com/community/Wacom") you linked to earlier you see it describes how to set up the extended input devices is Gimp and Inkscape.  You do something similar in Xournal etc.  Then in Gimp you point the eraser end to the little eraser icon and once it is assigned save it.  So eraser only works in programs that support it.

---

### Post by TheNerdAL on 2010-08-08
> **Favux said:**
> I'm hoping you mean the eraser on the stylus.  If you look near the bottom of the [Wacom wiki]("https://help.ubuntu.com/community/Wacom") you linked to earlier you see it describes how to set up the extended input devices is Gimp and Inkscape.  You do something similar in Xournal etc.  Then in Gimp you point the eraser end to the little eraser icon and once it is assigned save it.  So eraser only works in programs that support it.

Okay, thanks for all your help, I really appreciate it. :)

---

### Post by TheNerdAL on 2010-10-08
I now have Ubuntu 10.10 and it doesn't seem to work.

Will a mod move this to the Maverick Meerkat testing section? 

Thanks. :)

---

