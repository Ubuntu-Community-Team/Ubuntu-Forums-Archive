---
title: "mkjams: 77: Syntax error: &quot;{&quot; unexpected (expecting &quot;do&quot;)"
date: 2009-01-29
forum: Server Platforms
---

### Post by vramirez on 2009-01-29
I'm trying to install ingres2006 using a guide found in ubuntu documentation. The problem is that when I try to build ingres using the tar source option, everything goes well until the following step:

[I]Next, bootstrap the build. This includes building mkjam and mkjams, which automate the creation of Jamfiles, and then invoking mkjams to set up the build tree:

# cd $ING_SRC/tools/port/jam
# jam
# mkjams[/I]

After I type mkjams I receive the following error:

*mkjams: 77: Syntax error: "{" unexpected (expecting "do")*

Any idea on this?

I've tried to edit all mkjams found in directory /home/ingres/ingres2006-src/src/tools/port/jam but I just don't understand.

Thanks
Victor

---

