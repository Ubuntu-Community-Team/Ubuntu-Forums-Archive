---
title: "Preconfigure gnome shares per user"
date: 2011-03-31
forum: Server Platforms
---

### Post by spidernik84 on 2011-03-31
Hello,
I'm looking for a neat solution for this kind of need: we're looking for a way to deploy pre-configured gnome workstations on a large corporate network. The most interesting tool for preconfiguring gnome is sabayon, but it is not allowing to prepopulate nautilus bookmarks with gvfs samba shares (having a set of shares for the users preconfigured is a very easy task on Windows AD domains).

The easiest way seems to push a predefined .gtk-bookmarks file into the /home/<username> directory, further customized for the network share of the user (i.e. //myserver/<username>/share). The file .gtk-bookmarks can't contain variables, a solution that could have simplified the per-user bookmark a lot.

We're using Puppet to distribute the configuration, and here's the problem: how to instruct puppet to generate a customized file with the interpreted <username> variable, and how to tell puppet to place this file in /home/<username>? As far as I know, Puppet runs systemwide, preventing per-user operation.
Ideally, the file should be created only at first login to avoid existing bookmarks to be overwritten...

Alternative solutions are obviously welcome, even not involving Puppet (at least directly)!

Thank you!

---

