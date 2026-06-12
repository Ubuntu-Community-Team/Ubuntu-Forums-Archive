---
title: "Thoughts on diagnostic tools for a slow server ?"
date: 2022-09-01
forum: Server Platforms
---

### Post by gigi1335 on 2022-09-01
Hello,

I would like to make progress on the diagnosis of a performance drop (variable cause of the bottleneck: CPU, RAM, I/O or network) of a Linux.

1) For this, can you advise me on documents that describe the tools to use :

. I see top, atop and htop; finally can we summarize things by saying that the main advantage of each are: top is present on all Linux, htop is more user-friendly and atop is more complete (I/O and network in addition to CPU and RAM) which would make me prefer atop?

. I see iotop for I/O but what use is it if atop does the job?

. I see vmstat but I don't see its added value compared to the above mentioned tools?

. I see iostat but what use is it if iotop or atop does the job?

. I see ifstat for the network but what use is it if atop does the job?

- I see sar for system data collection. In which case is it necessary rather than the above mentioned snapshot tools?

2) can you advise me on documents describing the stress of each parameter (CPU, RAM, I/O or network) and the diagnostic scenario?

3) regarding DB servers and in particular PostgreSQL, what are the specifics of this type of diagnosis?

I'm sorry for the number of questions but I tried to go around the question of the performance of a Linux server and I think that your answers will interest more than one!

I thank you in advance.

---

### Post by TheFu on 2022-09-01
Individual tools are useful for quick diagnosis, but for overall performance of a server, we need to look at many aspects - about 50.  There are performance monitoring tools that run all the time and send their data back to a central performance graphing server for admins to look over, see trends, and help make decisions.  This is how professionals do it.  Tools like Cacti, sysusage, munin are typical.

These are not snap-shot-in-time tools.  They are long term monitoring solutions, so an admin can spot trends, submit budgets to meet the needs far in advance of the trends they see and, when needed, look into optimization for specific server processing.  This is all based on the different data that gets captured for a week, a month, 6-12 months.

I won't be answering all the questions asked. There are classes and books on those subjects.  You might locate a LUG in your country where senior administrators hang out and ask them.  Many LUGs have gone online for their meetings.

The tools that end-users want and the tools that professional admins use are different.  Having performance data from the last year when troubleshooting issues is key.  A 10 minute spike 3 hours ago, probably isn't that important, unless it happens again.
[https://www.howtoforge.com/how-to-install-cacti-on-ubuntu-20-04/](https://www.howtoforge.com/how-to-install-cacti-on-ubuntu-20-04/)
[https://ubuntu.com/server/docs/tools-munin](https://ubuntu.com/server/docs/tools-munin)
[https://github.com/darold/sysusage](https://github.com/darold/sysusage)
[https://www.cyberciti.biz/tips/top-linux-monitoring-tools.html](https://www.cyberciti.biz/tips/top-linux-monitoring-tools.html) - explains why the different values are useful

---

### Post by ameinild on 2022-09-02
I'm running a monitoring stack with:

[LIST]
[*][Grafana]("https://hub.docker.com/r/grafana/grafana") (Docker) 
[*][Prometheus]("https://hub.docker.com/r/prom/prometheus") (Docker) 
[*][Prometheus Node Exporter]("https://github.com/prometheus/node_exporter") (apt install on each server) 
[*][Node Exporter Full Dashboard]("https://grafana.com/grafana/dashboards/1860-node-exporter-full/") (for Grafana) 
[/LIST]
For me this works very well, and gives a good overview of all important server parameters. And you can tweak and add new dashboards to Grafana to see view specific areas.

For additional metrics (and especially networking), you can add [Prometheus SNMP Exporter]("https://github.com/prometheus/snmp_exporter") to the stack, which will give you additional networking information. I've created a [SNMP Exporter Dashboard]("https://grafana.com/grafana/dashboards/15297-prometheus-network-exporter/") to give a nice overview.

---

### Post by gigi1335 on 2022-09-06
Thanks for all your answers, guys !

I agree with you about using supervision for overall performance. However, if I need a immediate information about a new and sudden slowdown, I assume that the use of the tools I mentioned in my initial post is necessary. In this case, can someone answer to my questions in my initial post, please ?

Thanks in advance for your help.

Gilles

---

### Post by ameinild on 2022-09-06
I use htop for here-and-now stats. You should be able to see both CPU, memory, IO and networking using htop (maybe you need to configure which fields are displayed).

---

### Post by gigi1335 on 2022-09-06
> **ameinild said:**
> I use htop for here-and-now stats. You should be able to see both CPU, memory, IO and networking using htop (maybe you need to configure which fields are displayed).

Thanks a lot for your answer. Indeed, htop is quite complete, I will use it now. For network use by process, another tool like iftop is needed.

Gilles

---

### Post by ameinild on 2022-09-06
Here is another neat tip. Define the following functions:

```

# Show processes, sort by CPU usage
cpu() {
  if [[ -z $1 ]]
  then
    (( rows = 6 ))
  elif (( $1 > 0 ))
  then
    (( rows = $1 + 1 ))
  else
    (( rows = 6 ))
  fi
  ps -ax -eo user,pid,pcpu:5,pmem:5,rss:8=R-MEM,vsz:10=V-MEM,tty:6=TTY,stat:5,bsdstart:7,bsdtime:7,args | (read h; echo "$h"; sort -nr -k 3) | head "-$rows" | less -SEX
}

# Show processes, sort by memory usage
mem() {
  if [[ -z $1 ]]
  then
    (( rows = 6 ))
  elif (( $1 > 0 ))
  then
    (( rows = $1 + 1 ))
  else
    (( rows = 6 ))
  fi
  ps -ax -eo user,pid,pcpu:5,pmem:5,rss:8=R-MEM,vsz:10=V-MEM,tty:6=TTY,stat:5,bsdstart:7,bsdtime:7,args | (read h; echo "$h"; sort -nr -k 4) | head "-$rows" | less -SEX
}
```

Run them as part of your bash startup sequence (in [FONT=courier new].bashrc[/FONT]), or source them right away.

Now, you can run the command [FONT=courier new]cpu[/FONT] and [FONT=courier new]mem[/FONT] to see the processes which consume most CPU and memory. If you add a number as parameter, it will give you the X top processes, else it will default to top 5.

See if this process listing can help you identify any process that consumes too much CPU or memory.

---

### Post by TheFu on 2022-09-06
> **gigi1335 said:**
> Thanks a lot for your answer. Indeed, htop is quite complete, I will use it now. For network use by process, another tool like iftop is needed.

Gilles

You might want to look at Glances.  I find it and top and htop limiting compared to seeing the full trend that a true monitoring system provides.  Glances looks much like htop + saidar. [https://nicolargo.github.io/glances/](https://nicolargo.github.io/glances/)  It is in the Canonical repos and can be customized.

---

