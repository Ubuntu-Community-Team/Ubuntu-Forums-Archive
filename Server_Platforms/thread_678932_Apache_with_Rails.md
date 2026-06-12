---
title: "Apache with Rails"
date: 2008-01-26
forum: Server Platforms
---

### Post by ngms27 on 2008-01-26
Hi,

I've got Apache and Rails working (mostly) but have a very strange bug.

If I add some javascript it work great in webbrick but apache modifies the page e.g.

<script src="/javascripts/calendar.js?1175029065" type="text/javascript"></script>
<link href="/stylesheets/calendar.css?1174983795" media="screen" rel="Stylesheet" type="text/css" />

Where the ?1175029065 is coming from I don't know. As you can see this also affects stylesheets

Has anyone got any ideas?

---

### Post by Brazen on 2008-01-26
I don't know why but my Rails applications always do that, too.  They still work just fine though.

I would, however, highly suggest you use mongrel_cluster to run your 
Rails apps behind Apache.

---

