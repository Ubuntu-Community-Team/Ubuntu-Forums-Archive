---
title: "Lower level network shaping"
date: 2008-01-28
forum: Ubuntu Brainstorm
---

### Post by Mr. Picklesworth on 2008-01-28
Right now, setting download speeds in applications is a common necessity for a shared network. However, no two applications present that option the same way, and some don't present it at all!

I recently discovered a number of neat tools that fix this for me. One of them is called "wondershaper", which lets me change the downstream and upstream for a particular device, on the fly, for everything. The results are instant and quite satisfying.
There were other tools that could do the same idea for particular processes. It stood out to me that they all demanded to run the process themselves, but it doesn't seem like it would be impossible to selectively shape networking for a process once it is running.

One major benefit of the graphical user interface is that windows can be traced directly to processes. In this way, the user can select a window and have a program know exactly what process to kill / limit.

Granted, moving network speed limiting outwards sounds weird. How dare we pull control from the applications?
Actually, this is already being done for every other kind of resource! That is what "nice" is all about, for example. That is what the window management stuff is all about, with reserving space that programs can draw to. We are not expecting the program to manage system resources for us; the program just has to go with the flow, and the operating system keeps it all organized as the end user would like.

How to implement it?
This would be an upstream type of thing. Somebody will have to persuade the GNOME people. I think, done right, this would be a positive adjustment for GNOME since it simplifies the user interface in the way we like, while adding functionality across the desktop. No longer must you hunt across menus to find out how to limit network resource usage in Download Tool X; it is always in the same place. Big, big plus for usability, and that's not even counting the benefit of easily controlling network usage for the forward-thinking applications that *don't* think to include the option!
Yes, those programs are forward-thinking just as an application like Scribes which does not use tabs; they expect the operating system to handle what it is supposed to handle, leaving the task entirely up to it. These programs are not back seat drivers.

My thought would be a few additions to NetworkManager. One would be a slider somewhere that can be dragged to set a global download limit for a device. Then another option would allow the user to specify download limit for a particular process, with an interface much like xkill (except with an extra dialog afterwards).
Another possibility is that global and per-application network shaping could be built in to the System Monitor, although setting things like that has always seemed out of scope to me. Still, it has an interface to kill and set priority for processes, so changing network usage doesn't seem a huge stretch.

I've babbled enough. What are your thoughts?
Yes, I do realize that this will have to be pushed upstream. Regardless, that does not stop tests and patches from being done downstream ;)

---

