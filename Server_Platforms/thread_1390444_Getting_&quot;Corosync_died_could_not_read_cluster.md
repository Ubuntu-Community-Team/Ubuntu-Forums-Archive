---
title: "Getting &quot;Corosync died: could not read cluster configuration&quot; on cman startup"
date: 2010-01-25
forum: Server Platforms
---

### Post by lumix on 2010-01-25
My cluster.conf looks like:

```


  <cluster name="example" config_version="1">
         <clusternodes>
           <clusternode name="nd01">
             <fence>
               <method name="human">
                 <device name="manual" ipaddr="nd01"/>
               </method>
             </fence>
           </clusternode>
         </clusternodes>

         <fencedevices>
           <fencedevice name="manual" agent="fence_manual"/>
         </fencedevices>

  </cluster>


```


I'm really getting frustrated with this.  I'm finding no docs at all on setting up the basics of clustering on Ubuntu (or Debian for that matter).  I've seen links, but they are *not* basic.

---

### Post by stlsaint on 2010-01-25
sorry if this is of no help but im not familar with what it is your doing...im assuming clustering but i dont use ubuntu for this so i cant speak on it. Try visiting here. [ManCluster]("http://manpages.ubuntu.com/manpages/hardy/man5/cluster.conf.5.html")

---

### Post by lumix on 2010-01-26
I've long since set up a tent and wash station on that page, but thanks for at least answering.

---

