---
title: "Thinking of a compiz plugin. Window preview with scale"
date: 2009-07-16
forum: The Cafe
---

### Post by orlox on 2009-07-16
Well, last days, ive been thinking in starting a little project, a compiz plugin that uses scale to provide window previews.

I had though about this some time ago, but it came back to me while looking at some gnome-do docky blueprints at launchpad, where I find this:

[https://blueprints.launchpad.net/do/+spec/docky-expo-plugin](https://blueprints.launchpad.net/do/+spec/docky-expo-plugin)

There, the idea is given to be implemented as a docky plugin (it provides a simple screencast also), but I think it could be taken much further, and implemented as a compiz plugin so it could work not only with docky.

Although, the greatest drawback from this idea, is that the scale plugin doesnt show minimized windows, but still, I would find this feature very useful.

Lets take for instance, the window previews plugin:

[http://wiki.compiz-fusion.org/Plugins/Thumbnail](http://wiki.compiz-fusion.org/Plugins/Thumbnail)

This one shows a thumbnail of a window that is in the taskbar by hovering over it. The interesting thing, is that it works with the regular gnome window list and gnome-do's docky.

Now, what if instead of a window preview (which is nothing more that an image that you cant interact with), hovering over an item in the window list displayed all of the windows corresponding to that item using the well-known scale compiz plugin:

[http://wiki.compiz-fusion.org/Plugins/Scale](http://wiki.compiz-fusion.org/Plugins/Scale)

I've started trying to do this. I did the most basic plugin possible which does nothing but it compiles successfully and appears listed in the compiz manager.

I know the scale plugin can be extended to filter specific windows (the "scale window title filter" plugin does it), and I'm trying to start the development of this plugin by looking at the code of the window previews plugin, but I find it rather complicated, since the documentation on APIs an on how to extend the scale plugin is mostly unexistant (or at least I havent found it)...

Does anyone know of a good starting point to learn how to create plugins for compiz?? The documentation provided in the compiz website is pretty scarce...it seems the only way would be to start crawling through the (mostly) uncommented code of the other plugins. Even though, I think much of the knowledge needed could be obtained by studying the existing plugins mentioned above.

Ideas, comments or help are, of course, welcome...hope you like this idea!

---

