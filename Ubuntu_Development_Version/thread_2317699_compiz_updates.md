---
title: "compiz updates"
date: 2016-03-18
forum: Ubuntu Development Version
---

### Post by ventrical on 2016-03-18
Updates to all components. I got 3D windows back, water effects, wobbly, cube n' roll .. but the cylinder is not working right still and no cube gears.

---

### Post by mc4man on 2016-03-18
Those were fixed in wily, (August for 3d),  didn't work for you till now?

---

### Post by ventrical on 2016-03-18
Not the 3D windows feature. It was all broken and jagged. Hmmm as I reflect, I haven't really been using it that much. I made a comment about compiz in another forum and I thought they had all but abandoned it completely until today's updates. Thanks for the info on fixes in August.

---

### Post by mc4man on 2016-03-18
Everytime they update compiz I have a thing or 2 I want changed so in the process always see the changelog. For your viewing pleasure when slow the last 6 months or so..
> compiz (1:0.9.12.2+16.04.20160318-0ubuntu1) xenial; urgency=medium

  [ Alberts Muktup&#257;vels ]
  * gtk-window-decorator: Use the Marco gsettings in MATE session.
  * gtk-window-decorator: add support for dark theme variant.

  [ Martin Wimpress ]
  * MATE Compiz configuration is now consistent with composited Marco
    and Metacity.

 -- Marco Trevisan (Treviño) <mail@3v1n0.net>  Fri, 18 Mar 2016 10:08:19 +0000

compiz (1:0.9.12.2+16.04.20160311-0ubuntu1) xenial; urgency=medium

  [ Alberts Muktup&#257;vels ]
  * Avoid GtkStyleContext warnings with GTK+ 3.20+.
  * Remove GWDSettingsXPropertyStorageInterface.
  * gtk-window-decorator: Remove unused setting from mutter.

  [ Martin Wimpress ]
  * mate.ini: Enable 'Keep Minimzed Windows' by default for the MATE
    profile (LP: #1067951)

  [ Sam Spilsbury [email]smspillaz@gmail.com[/email] ]
  * Fix broken tests

 -- Marco Trevisan (Treviño) <mail@3v1n0.net>  Fri, 11 Mar 2016 08:26:45 +0000

compiz (1:0.9.12.2+16.04.20160209-0ubuntu1) xenial; urgency=medium

  [ Eleni Maria Stea ]
  * chrome and chromium windows are considered compiz windows in
    fullscreen to avoid tearing (Bug #1442728) (LP: #1442728)

 -- Marco Trevisan (Treviño) <mail@3v1n0.net>  Tue, 09 Feb 2016 01:16:01 +0000

compiz (1:0.9.12.2+16.04.20151211-0ubuntu1) xenial; urgency=medium

  [ Marco Trevisan (Treviño) ]
  * FindXorgGTest: escape unscaped quotes on pkg-config variables (LP:
    #1521366)
  * Scale: use current monitor workarea to check whether the mouse is
    inside or not (LP: #1516599)
  * backends: drop gconf support

  [ Sebastien Bacher ]
  * Update the apport hook, get the gsettings config not the gconf one
    (LP: #1508974)

 -- Marco Trevisan (Treviño) <mail@3v1n0.net>  Fri, 11 Dec 2015 10:00:39 +0000

compiz (1:0.9.12.2+16.04.20151026-0ubuntu1) xenial; urgency=medium

  * Move: remember the type of movement and use the proper grabbing for
    it (LP: #1487637)
  * Resize: remember the type of movement and use the proper grabbing
    for it (LP: #1487637)
  * Screen: add cursorChangeNotify function and call it on
    XA_RESOURCE_MANAGER
  * Screen: add pushKeyboardGrab and pushPointerGrab methods to add
    different kinds of grabs
  * Screen: monitor root RESOURCE_MANAGER and update cursors when Size
    or Theme changes (LP: #1359211)

 -- Marco Trevisan (Treviño) <mail@3v1n0.net>  Mon, 26 Oct 2015 17:15:54 +0000

compiz (1:0.9.12.2+15.10.20151015-0ubuntu1) wily; urgency=medium

  [ Marco Trevisan (Treviño) ]
  * Syncing changelog with proposed

  [ CI Train Bot ]
  * No-change rebuild.

 -- Marco Trevisan (Treviño) <mail@3v1n0.net>  Thu, 15 Oct 2015 16:13:32 +0000

compiz (1:0.9.12.2+15.10.20151002-0ubuntu1) wily; urgency=medium

  [ Eleni Maria Stea ]
  * Fixes the texture coordinates of the cube and deformed cube caps so
    that the top and bottom images appear centered. (LP: #1498504)

  [ Marco Trevisan (Treviño) ]
  * TestPrivateScreen: ignore unused init const. (LP: #1499108)

 -- Marco Trevisan (Treviño) <mail@3v1n0.net>  Fri, 02 Oct 2015 00:31:47 +0000

compiz (1:0.9.12.2+15.10.20150908-0ubuntu1) wily; urgency=medium

  [ Stephen M. Webb ]
  * new upstream version 0.9.12.2
  * debian/upstream: added signing key

  [ Andrea Azzarone [email]andrea.azzarone@canonical.com[/email] ]
  * Build compiz using c++11.
  * Enable building compiz from sources using cmake3.

  [ Artur drozd ]
  * Allow to select background color for switcher and staticswitcher.
    (LP: #1329811)

  [ Eleni Maria Stea ]
  * decoration: fixed warning for parentheses order

  [ Tim Lunn ]
  * Remove unused code that causes a build-dep on gnome-control-center-
    dev (LP: #1481541) (LP: #1481541)

 -- Marco Trevisan (Treviño) <mail@3v1n0.net>  Tue, 08 Sep 2015 11:36:16 +0000

compiz (1:0.9.12.1+15.10.20150805-0ubuntu1) wily; urgency=medium

  [ Alberts Muktup&#257;vels ]
  * Change icon size back to 48px in application switcher plugin. (LP:
    #1237057)

  [ CI Train Bot ]
  * New rebuild forced.

  [ Dmitry Shachnev ]
  * Move window switcher plugins to compiz-plugins-default. (LP:
    #971051, #1465647)
  * debian/compiz-gnome.gsettings-override: Remove unityshell from
    active plugins, and add switcher. (LP: #1469086)

  [ Eleni Maria Stea ]
  * It fixes the 3d windows plugin. Problem: The 3d clipping is
    performed in viewing space (modelview transformation) and should be
    done inside the shader when we use shaders otherwise the viewing
    space pipeline operations will be ignored. Compiz used to perform
    the clipping inside the td plugin using pipeline functions, then it
    was loading a generic shader program (no clipping operations) to
    render the windows and then it rendered the 3d quads around the
    windows using the pipeline (so these were clipped correctly). (LP:
    #1395697)
  * Sometimes the MultipleCubes, Automatic or OneBigCube option might be
    set although we are not in multimonitor. Modified the 3d windows
    plugin to check the number of monitors as well.

  [ Marco Trevisan (Treviño) ]
  * Window: add clientFrame(), to get the client-side decoration extents
    (LP: #1422768, #1436553)
  * Window: compute the correct output using the absolute window
    position (LP: #1475721)

  [ Martin Wimpress ]
  * align MATE profile more closely with Marco

  [ Stephen M. Webb ]
  * Fix a FTBFS when -std=c++11 is used. (LP: #1477654)
  * Fixed the Compiz manpage and --help message to agree with the actual
    command-line options supported. (LP: #1475508)
  * force Compiz to build using C++-11 (required by build dependency
    libgtkmm-3.0-1). (LP: #1477978)

 -- CI Train Bot <ci-train-bot@canonical.com>  Wed, 05 Aug 2015 11:26:51 +0000


---

