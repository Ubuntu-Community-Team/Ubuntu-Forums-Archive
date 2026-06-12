---
title: "feh bg scale only?"
date: 2007-09-26
forum: The Cafe
---

### Post by aimran on 2007-09-26
So far after searching most of the feh commands for wallpaper only has scale:

```
feh --bg-scale /home/you/wallpaper.jpg
```

Is scale the only option? I tried zoom but doesn't work :P

Is there any other wallpaper setter option out therE?

---

### Post by Lord Illidan on 2007-09-26
What are you trying to do with feh?

---

### Post by aimran on 2007-09-26
Set a wallpaper I guess?

---

### Post by init1 on 2007-09-26
> **aimran said:**
> So far after searching most of the feh commands for wallpaper only has scale:

```
feh --bg-scale /home/you/wallpaper.jpg
```

Is scale the only option? I tried zoom but doesn't work :P

Is there any other wallpaper setter option out therE?
I use Esetroot.
```

apt-get install eterm
Esetroot yourimage.ext

```

---

### Post by kerry_s on 2007-09-26
it's just hard to read in the terminal, what i do is transfer it to a txt file so i can read it in my editor. just use> 
command >> any-name.txt
example:
feh -h >> help.txt
or
man feh >> feh.txt

then just open the txt file in your home directory.

--bg-tile FILE
--bg-center FILE
--bg-seamless FILE
-s, --stretch

```

Usage : feh [OPTIONS]... FILES...
 Where a FILE is an image file or a directory.
 Multiple files are supported.
 Urls are supported. They must begin with http:// or ftp:// and you must
 have wget installed to download the files for viewing.
 Options can also be specified in the in the feh configuration file. See
 man feh for more details
 -h, --help                display this help and exit
 -v, --version             output version information and exit
 -V, --verbose             output useful information, progress bars, etc
 -q, --quiet               Don't report non-fatal errors for failed loads
                           Verbose and quiet modes are not mutually exclusive,
                           the first controls informational messages, the
                           second only errors.
 -T, --theme THEME         Load options from config file with name THEME
                           see man feh for more info.
     --rcfile FILE         Use FILE to parse themes and options from,
                           instead of the default ~/.fehrc, /etc/fehrc files.
 -r, --recursive           Recursively expand any directories in FILE to
                           the content of those directories. (Take it easy)
 -z, --randomize           When viewing multiple files in a slideshow,
                           randomise the file list before displaying
 --no-jump-on-resort       Don't jump to the first image when the filelist
                           is resorted.
 -g, --geometry STRING     Limit (and don't change) the window size. Takes
                           an X-style geometry string like 640x480.
                           Note that larger images will be zoomed out to fit
                           but you can see them at 1:1 by clicking the zoom
                           button.
 -f, --filelist FILE       This option is similar to the playlists used by
                           music software. If FILE exists, it will be read
                           for a list of files to load, in the order they
                           appear. The format is a list of image filenames,
                           absolute or relative to the current directory,
                           one filename per line.
                           If FILE doesn't exist, it will be created from the
                           internal filelist at the end of a viewing session.
                           This is best used to store the results of complex
                           sorts (-Spixels for example) for later viewing.
                           Any changes to the internal filelist (such as
                           deleting a file or it being pruned for being
                           unloadable) will be saved to FILE when feh exits.
                           You can add files to filelists by specifying them
                           on the commandline when also specifying the list.
 -p, --preload             Preload images. This doesn't mean hold them in
                           RAM, it means run through and eliminate unloadable
                           images first. Otherwise they will be removed as you
                           flick through.
     --scale-down          Automatically scale down images too big for the
                           screen. Currently only works with -P
 -F, --full-screen         Make the window fullscreen
 -Z, --auto-zoom           Zoom picture to screen size in fullscreen mode,
                           is affected by the option --stretch
     --zoom PERCENT        Zooms images by a PERCENT, when in full screen
                           mode or when window geometry is fixed. If combined
                           with --auto-zoom, zooming will be limited to the
                           the size.
 -w, --multiwindow         Disable slideshow mode. With this setting,
                           instead of opening multiple files in slideshow
                           mode, multiple windows will be opened.
 -x, --borderless          Create borderless windows
 -d, --draw-filename       Draw the filename at the top-left of the image.
     --title TITLE         Use TITLE as the window title in slideshow mode.
 -D, --slideshow-delay NUM For slideshow mode, specifies time delay (seconds,
                           can be a decimal) between automatically changing
                           slides.
     --cycle-once          exit feh after one loop through a slideshow
 -R, --reload NUM          Use this option to tell feh to reload an image
                           after NUM seconds. Useful for viewing webcams
                           via http, or even on your local machine.
 -Q, --builtin             Use builtin http grabber to grab remote files
                           instead of wget.
                           mechanism, useful if don't have wget.
 -k, --keep-http           When viewing files using http, feh normally
                           deletes the local copies after viewing, or,
                           if caching, on exit. This option prevents this
                           so that you get to keep the local copies.
                           They will be in the current working directory
                           with "feh" in the name.
     --caption-path PATH   Path to directory containing image captions.
                           This turns on caption viewing, and if captions
                           are found in PATH, which is relative to the
                           directory of each image, they are overlayed
                           on the displayed image.
                           e.g with caption path "captions", and viewing
                           image images/foo.jpg, caption will be looked for
                           as "images/captions/foo.jpg.txt"
 -j, --output-dir          Output directory for saved files.  Really only
                           useful with the -k flag.
 -G, --wget-timestamp      When viewing http images with reload set (eg
                           webcams), try to only reload the image if the
                           remote file has changed.
 -l, --list                Don't display images. Analyse them and display an
                           'ls' style listing. Useful in scripts hunt out
                           images of a certain size/resolution/type etc.
 -L, --customlist FORMAT   Use FORMAT as the format specifier for list
                           output. FORMAT is a printf-like string containing
                           image info specifiers. See FORMAT SPECIFIERS.
 -U, --loadable            Don't display images. Just print out their name
                           if imlib2 can successfully load them.
 -u, --unloadable          Don't display images. Just print out their name
                           if imlib2 can NOT successfully load them.
 -S, --sort SORT_TYPE      The file list may be sorted according to image
                           parameters. Allowed sort types are: name,
                           filename, width, height, pixels, size, format.
                           For sort modes other than name or filename, a
                           preload run will be necessary, causing a delay
                           proportional to the number of images in the list
 -n, --reverse             Reverse the sort order. Use this to invert the order
                           of the filelist. Eg to sort in reverse width order,
                           use -nSwidth
 -A, --action ACTION       Specify a string as an action to perform on the
                           image. In slideshow or multiwindow modes, the action
                           in list mode, or loadable|unloadable modes, the
                           action will be run for each file.
                           The action will be executed by /bin/sh. Use
                           format specifiers to refer to image info. See
                           FORMAT SPECIFIERS for examples
                           Eg. -A "mv %f ~/images/%n"
                           In slideshow mode, the next image will be shown
                           after running the command, in multiwindow mode,
                           the window will be closed.
     --action1 ACTION      These extra action options allow you to specify
     --action2 ACTION      multiple additional actions which can be invoked
     ...                   using the appropriate number key 1-9
     --action9 ACTION
 -m, --montage             Enable montage mode. Montage mode creates a new
                           image consisting of a grid of thumbnails of the
                           images specified using FILE... When montage mode
                           is selected, certain other options become
                           available. See MONTAGE MODE OPTIONS
 -c, --collage             Same as montage mode, but the thumbnails are
                           distributed randomly. You must specify width and
                           height or supply a background image or both
 -i, --index               Enable Index mode. Index mode is similar to
                           montage mode, and accepts the same options. It
                           creates an index print of thumbails, printing the
                           images name beneath each thumbnail. Index mode
                           enables certain other options, see INDEX MODE
                           OPTIONS
 -t, --thumbnails          As --index, but clicking an image will open it in
                           a new viewing window
     --cache-thumbnails    Enable thumbnail caching
 -I, --fullindex           Same as index mode, but below each thumbnail you
                           get image name, size and dimensions
     --bg-tile FILE
     --bg-center FILE
     --bg-scale FILE
     --bg-seamless FILE    Set your desktop background to FILE. Feh can
                           use enlightenment IPC if you are running it,
                           or will fall back to X methods.
                           Feh stores the commandline necessary to restore
                           the background you chose in ~/.fehbg. So to have
                           feh-set backgrounds restored when you restart X,
                           add the line "eval `cat $HOME/.fehbg`" to your
                           X startup script (e.g. ~/.xsession). Note that
                           you only need to do this for non E window
                           managers.
     --fontpath PATH       Specify an extra directory to look in for fonts,
                           can be used multiple times to add multiple paths.
 -M, --menu-font FONT      Use FONT for the font in menus.
     --menu-style FILE     Use FILE as the style descriptor for menu text.
     --menu-bg BG          Use BG for the background image in menus.
     --menu-border INT     Specify number of pixels that define the menu
                           background's border. Borders are not stretched
                           when images are scaled.
 -N, --no-menus            Don't load or show any menus.
 -1, --next-button B       Use button B to advance to the next image in any
                           mode (defaults to 1, usually the left button).
 -2, --zoom-button B       Use button B to zoom the current image in any
                           mode (defaults to 2, usually the middle button).
 -4, --menu-button B       Use CTRL+Button B to activate the menu in any
                           mode.  Set to 0 for any button.  This option
                           is disabled if the -N or --no-menus option is set
                           (defaults to 3, usually the right button).
 -5, --menu-ctrl-mask      Require CTRL+Button for menu activation in
                           any mode (default=off).
 -6, --rotate-button B     Use CTRL+Button B to rotate the current image in
                           any mode (default=2).
 -7, --no-rotate-ctrl-mask Don't require CTRL+Button for rotation in
                           any mode -- just use the button (default=off).
 -8, --blur-button B       Use CTRL+Button B to blur the current image in
                           any mode (default=1).
 -9, --no-blur-ctrl-mask   Don't require CTRL+Button for blurring in
                           any mode -- just use the button (default=off).
     --xinerama [0|1]      Enable/disable Xinerama support.  Has no effect
                           unless you have an Xinerama compiled in.
     --screen-clip [0|1]   Enable/disable window clipping based on screen
                           size.  WARNING: with this option disabled,
                           image windows could become very large, making
                           them unmanageable in certain window managers.
     --hide-pointer        In full screen mode, hide the X mouse pointer.
 FORMAT SPECIFIERS
                           %f image path/filename
                           %n image name
                           %s image size (bytes)
                           %p image pixel size
                           %w image width
                           %h image height
                           %t image format
                           %P prints feh
                           %v prints the version
                           %m prints the mode (slideshow, multiwindow...)
                           %l prints the total number of files in the filelist
                           %u prints the current file number
                           \n prints a newline
                           Eg. feh -A "mv %f ~/images/%n" *
 MONTAGE MODE OPTIONS
 -X, --ignore-aspect       By default, the montage thumbnails will retain
                           their aspect ratios, while fitting in --thumb-width
                           and --thumb-height. This option will force them to
                           be the size set by --thumb-width and --thumb-height
                           This will prevent any whitespace in the final
                           montage
 -s, --stretch             Normally, if an image is smaller than the specified
                           thumbnail size, it will not be enlarged. If this
                           option is set, the image will be scaled up to fit
                           the thumbnail size. (Aspect ratio will be maintained
                           unless --ignore-aspect is specified)
 -y, --thumb-width NUM     Set thumbnail width in pixels
 -E, --thumb-height NUM    Set thumbnail height in pixels
                           Thumbnails default to 20x20 pixels
 -W, --limit-width NUM     Limit the width of the montage in pixels
 -H, --limit-height NUM    Limit the height of the montage in pixels
                           These options can be used together (to define the
                           image size exactly), or separately. If only one is
                           specified, theother is calculated from the number
                           of files specified and the size of the thumbnails.
                           The default is to limit width to 800 pixels and
                           calculate the height
 -b, --bg FILE|trans       Use FILE as a background for your montage. With
                           this option specified, the size of the montage will
                           default to the size of FILE if no size restrictions
                           are specified. Alternatively, if FILE is "trans",
                           make the background transparent.
 -a, --alpha NUM           When drawing thumbnails onto the background, apply
                           them with a transparency level of NUM (0-255).
 -o FILE                   Save the created montage to FILE
 -O FILE                   Just save the created montage to FILE
                           WITHOUT displaying it (use in scripts)
 INDEX MODE OPTIONS
 -e FONT                   Use FONT to print the information under each
                           thumbnail. FONT should be defined in the form
                           fontname/size(points). eg -e myfont/12
 -t, --title-font FONT     Use FONT to print a title on the index, if no
                           font is specified, a title will not be printed
 SLIDESHOW KEYS
 The default mode for viewing mulitple images is Slideshow mode
 When viewing a slideshow, the following keys may be used:
 p, P, <BACKSPACE>, <LEFT>  Goto previous slide
 n, N, <SPACE>, <RIGHT>     Goto next slide
 r, R                       Reload image (good for webcams)
 v, V                       Toggle fullscreen
 m, M                       Show popup menu
 c, C                       Caption entry mode. If --caption-path has been
                            specified, then this enables caption editing.
                            The caption will turn yellow and be editable,
                            hit enter to confirm and save the caption, or
                            hit escape to cancel and revert the caption.
 w, W                       Size window to current image dimensions
 h, H                       Pause the slideshow (only useful when using
 s, S                       Save current image to unique filename
 f, F                       Save current filelist to unique filename
                            timed reloading or image changes)
 <, >                       In place editing, rotate 90 degrees right/left
 <HOME>                     Goto first slide
 <END>                      Goto last slide
 <ESCAPE>                   Quit the slideshow
 +, =                       Increase reload delay
 -, _                       Decrease reload delay
 <DELETE>                   Remove the currently viewed file from the filelist
 <CTRL+DELETE>              Delete the currently viewed file and remove it
                            from the filelist
 x, X                       Close current window
 q, Q                       Quit the slideshow
 <KEYPAD LEFT>              Move the image to the left
 <KEYPAD RIGHT>             Move the image to the right
 <KEYPAD +>                 Zoom in
 <KEYPAD ->                 Zoom out
 <KEYPAD *>                 Zoom to 100%
 <KEYPAD />                 Zoom to fit the window
 <ENTER>,0                  Run action specified by --action option
 1-9                        Run action 1-9 specified by --action[1-9] options

 MOUSE ACTIONS
 When viewing an image, a click of mouse button 1 moves to the next image
 (slideshow mode only), a drag of mouse button 1 pans the image, if the
 viewable window is smaller than the image, button 2 zooms (click and drag
 left->right to zoom in, right->left to zoom out, click once to restore
 1x zoom), and mouse button 3 pans.
 Ctrl+button 1 blurs or sharpens the image (drag left to blur and right to
 sharpen).  Ctrl+button 2 rotates the image around the center point.
 Button 3 activates the context-sensitive menu.  Buttons can be redefined
 with the -1 through -9 (or --*-button) cmdline flags.  All you people
 with million button mice can remove the ctrl mask with the --no-*-ctrl-mask
 options.

See 'man feh' for more detailed information

This program is free software see the file COPYING for licensing info.
Copyright Tom Gilbert (and various contributors) 1999-2003
Email bugs to <feh_sucks@linuxbrit.co.uk>


```

---

### Post by aimran on 2007-09-26
Thanks alot for the replies :)

---

### Post by fuscia on 2007-09-27
*feh -m /filewithallyourwallpapers*, right-click on the one you want, file>background>take your pick...

---

