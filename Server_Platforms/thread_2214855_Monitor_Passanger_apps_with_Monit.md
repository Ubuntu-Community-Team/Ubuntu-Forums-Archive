---
title: "Monitor Passanger apps with Monit"
date: 2014-04-03
forum: Server Platforms
---

### Post by hunterlove22 on 2014-04-03
[COLOR=#000000][FONT=Arial]I have rails app running under the passenger process. I want to have monit to monitor the background.[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]The command to start is:[/FONT][/COLOR]
> RAILS_ENV=production QUEUE=* rake resque:work
[COLOR=#000000][FONT=Arial]I just want get the resque workers to start up and restart when they crash.[/FONT][/COLOR]

---

### Post by rubylaser on 2014-04-03
I would do this with  [Foreman and Upstart]("http://jasonroelofs.com/2012/03/12/manage-and-monitor-resque-with-upstart-and-monit/") if you had to.  But, I would use [Sidekiq]("http://jasonroelofs.com/2013/10/08/managing-resque-with-upstart/") instead of resque.

---

### Post by hunterlove22 on 2014-04-03
> **rubylaser said:**
> I would do this with  [Foreman and Upstart]("http://jasonroelofs.com/2012/03/12/manage-and-monitor-resque-with-upstart-and-monit/") if you had to.  But, I would use [Sidekiq]("http://jasonroelofs.com/2013/10/08/managing-resque-with-upstart/") instead of resque.

Thanks. I don't want to anything with code.

In his post, there is ERB configuration:

```
[COLOR=#999999][FONT=Consolas]**<%**[/FONT][/COLOR][COLOR=#000000][FONT=Consolas] [/FONT][/COLOR][COLOR=teal][FONT=Consolas]@worker_count[/FONT][/COLOR][COLOR=#000000][FONT=Consolas]**.**[/FONT][/COLOR][COLOR=#000000][FONT=Consolas]times[/FONT][/COLOR][COLOR=#000000][FONT=Consolas] [/FONT][/COLOR][COLOR=#000000][FONT=Consolas]**do**[/FONT][/COLOR][COLOR=#000000][FONT=Consolas] [/FONT][/COLOR][COLOR=#000000][FONT=Consolas]**|**[/FONT][/COLOR][COLOR=#000000][FONT=Consolas]i[/FONT][/COLOR][COLOR=#000000][FONT=Consolas]**|**[/FONT][/COLOR][COLOR=#000000][FONT=Consolas] [/FONT][/COLOR][COLOR=#999999][FONT=Consolas]**-%>**[/FONT][/COLOR]check process resque-[COLOR=#999999]**<%=**[/COLOR] i [COLOR=#999999]**-%>**[/COLOR] with pidfile [COLOR=#999999]**<%=**[/COLOR] [COLOR=teal]@project_root[/COLOR] [COLOR=#999999]**-%>**[/COLOR]/shared/pids/resque-[COLOR=#999999]**<%=**[/COLOR] i [COLOR=#999999]**-%>**[/COLOR].pid
  group resque
  start program = "/sbin/start resque ID=[COLOR=#999999]**<%=**[/COLOR] i [COLOR=#999999]**-%>**[/COLOR]"
  stop program = "/sbin/stop resque ID=[COLOR=#999999]**<%=**[/COLOR] i [COLOR=#999999]**-%>**[/COLOR]"
  if changed pid 6 times within 6 cycles then stop
 
[COLOR=#999999][FONT=Consolas]**<%**[/FONT][/COLOR][COLOR=#000000][FONT=Consolas] [/FONT][/COLOR][COLOR=#000000][FONT=Consolas]**end**[/FONT][/COLOR][COLOR=#000000][FONT=Consolas] [/FONT][/COLOR][COLOR=#999999][FONT=Consolas]**%>**[/FONT][/COLOR]
```

Where can i put it? in to monit's configuration file or anywhere? Coz this looks different from monit's standard configuration.

---

### Post by rubylaser on 2014-04-03
This is a chef recipe and it was just an example.  Here's another easier [example]("https://stackoverflow.com/questions/12094311/managing-resque-workers-with-monit-on-rbenv-setup") that is in the comments on Ryan Bate's Monit Railscast.

---

### Post by hunterlove22 on 2014-04-05
> **rubylaser said:**
> This is a chef recipe and it was just an example.  Here's another easier [example]("https://stackoverflow.com/questions/12094311/managing-resque-workers-with-monit-on-rbenv-setup") that is in the comments on Ryan Bate's Monit Railscast.

Thank you so much. I will check it.

---

