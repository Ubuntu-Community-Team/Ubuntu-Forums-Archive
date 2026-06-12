---
title: "Torque under 12.04: jobs won't start"
date: 2012-10-18
forum: Server Platforms
---

### Post by spacemen12 on 2012-10-18
Hi,
   I've tried to setup a pbs for my desktop computer 6 core.

   The queing system seems to work, but I cannot get the jobs to run, even with qrun.

```
me@haldane:DIR.torque $ echo "sleep 30" | qsub
15.haldane
me@haldane:DIR.torque $ qstat
Job id                    Name             User            Time Use S Queue
------------------------- ---------------- --------------- -------- - -----
15.haldane                 STDIN            me                    0 Q batch          
me@haldane:DIR.torque $ qrun 15
qrun: Unauthorized Request  15.haldane
```

Some config

```
me@haldane:DIR.torque $ qmgr -c "list server"
Server haldane
	server_state = Active
	scheduling = True
	total_jobs = 1
	state_count = Transit:0 Queued:1 Held:0 Waiting:0 Running:0 Exiting:0 
	acl_hosts = haldane
	default_queue = batch
	log_events = 511
	mail_from = adm
	query_other_jobs = True
	scheduler_iteration = 600
	node_check_rate = 150
	tcp_timeout = 6
	pbs_version = 2.5.12
	next_job_number = 16
	net_counter = 1 0 0

me@haldane:DIR.torque $ qmgr -c "list queue batch"
Queue batch
	queue_type = Execution
	total_jobs = 1
	state_count = Transit:0 Queued:1 Held:0 Waiting:0 Running:0 Exiting:0 
	resources_max.ncpus = 12
	resources_default.nodes = 1
	resources_default.walltime = 01:00:00
	mtime = Thu Oct 18 15:55:08 2012
	enabled = True
	started = True
me@haldane:DIR.torque $ pbsnodes -a
haldane
     state = down
     np = 12
     ntype = cluster
     gpus = 0


```

---

