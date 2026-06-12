---
title: "BENCHMARKS - RAID and disk I/O performance"
date: 2010-03-28
forum: Server Platforms
---

### Post by jrssystemsnet on 2010-03-28
OK guys, as promised, here is some nice shiny data.  (All images are clickable if you want an embiggenated version.)

First, a brief description of how these numbers were generated and why:

40GB of binary data is dumped into the test platform before the tests begin.  During each test, one to five read processes make random-access reads of the 40GB binary file as quickly as they can, while a write process appends data to one of ten random files on the test platform several times per second.

This produces raw data on performance at a given read chunk size, for 1 to 5 concurrent read processes, under three different levels of concurrent writes.  I dump this data into a spreadsheet as it comes in from the terminal; a completed test run for a given platform at a given test size looks like this:

[[img]http://virtual.tehinterweb.net/livejournal/2010-03-26_raidperformance/thumbs/2010-03-26_raw_data_sample.png[/img]](http://virtual.tehinterweb.net/livejournal/2010-03-26_raidperformance/2010-03-26_raw_data_sample.png)

The reason I'm doing things this way is because I want to approximate the life of a really heavily loaded workstation or fileserver as closely as possible, and I want to know exactly what is going on in the benchmarking process.  So I want a model that is heavily weighted towards reads, with just enough writes thrown in to make things interesting - most I/O platforms do noticeably worse on a mixed load than they do with pure reads! - and I want to minimize the effect of caching, but not necessarily invalidate it *completely*.  Again, the idea is "model a fileserver or workstation on a bad day", not "isolate a single factor in a heavily synthetic benchmark".

The test hardware is a Q8300 quad-core Intel CPU on an ASUS motherboard, 4GB DDR2 SDRAM, and FreeBSD 8.0-R amd64 / Ubuntu 9.10 Server amd64 as appropriate.  The drives tested are Western Digital Caviar Black 1TB drives, both singly and in 6-drive RAID configurations, and an Intel X-25M SSD.

With that said... on to the shinies. :popcorn:

[[img]http://virtual.tehinterweb.net/livejournal/2010-03-26_raidperformance/thumbs/2010-03-26_raid_performance_average_linear.png[/img]](http://virtual.tehinterweb.net/livejournal/2010-03-26_raidperformance/2010-03-26_raid_performance_average_linear.png)

This is the simplest graph; we boiled it down to average read throughput at each chunk size; so that a single number for each size represents all three write process types and all five numbers of concurrent read processes.  There are a few things to notice here.

First: EVERYTHING sucks at really small reads.  But although everything sucks at really small reads, SSDs suck at it a lot less than any combination of conventional drives.  The Intel X25-M SSD delivered 5.6 MB/sec averaged throughput on 16k reads, compared to 2.0 MB/sec for the WD 1TB drive using the deadline scheduler, and 2.8MB/sec for mdraid5 using *six* 1TB drives.  (RAIDZ was by far the worst performer at tiny reads, delivering only 1.1 MB/sec.)

Second: for read-biased mixed read/write workloads... mdraid5 outperforms mdraid10 pretty much across the board.  Of course, this isn't the entire story; a more heavily write-biased workload might favor the mdraid10 more.  (Raw write performance on the mdraid5 was 194MB/sec; on the mdraid10 it was 245MB/sec.)  

Third: when it comes to performance, the underlying storage hardware is by far the most important ingredient.  The best performer here was a single Intel X25-M SSD... and the next step down was the same Intel X25-M SSD running ZFS, leaving six-drive arrays of slower hardware in the dust.  This is true even when it comes to faster drives of the same basic type; the single-drive performance of the Caviar Black tested here is better than the RAID5 performance of an entire array of Seagate Barracuda 750GB drives I tested last year.

Fourth: notice that there are two entries for ext4 on a single 1TB drive marked "deadline" and "cfq".  This is the exact same drive and filesystem running under two different I/O schedulers; cfq stands for Completely Fair Queueing and outperforms deadline everywhere except 16k and 128k reads.  But there's more there than meets the eye; we'll return to that later.

Next slide, please:

[[img]http://virtual.tehinterweb.net/livejournal/2010-03-26_raidperformance/thumbs/2010-03-26_raid_performance_detailed_linear.png[/img]](http://virtual.tehinterweb.net/livejournal/2010-03-26_raidperformance/2010-03-26_raid_performance_detailed_linear.png)

In the detailed graph, we examine performance levels for the tested platforms not only at each chunk size, but also at each number of concurrent processes.  We started this graph at 128k chunk size, because that's where the differences really start showing up.

The SSD, of course, leads the pack by a mile - although interestingly, we see that mdraid5 actually outperforms it, just barely, at one single level - 5mb reads, one read process only.  It's also interesting to note how relatively smooth the graph is for mdraid10 - while mdraid5 outperforms it almost entirely across the board, mdraid10 is a much more *predictable* performer.

It's also interesting to notice how closely the performance of a single drive under ZFS mirrors the performance of a six-drive RAIDZ array of the same drives - the shape is identical, even down to the weird tweaky peaks in performance at 1 and 3 concurrent processes and valleys at 2 and 4 processes.  This suggests that there is probably a lot of room for optimization in RAIDZ's algorithms... and serves as a warning for anybody looking for raw performance; across most of the graph the single-disk ZFS performs better than the six-drive RAIDZ array.

Now, let's take a closer look at those I/O schedulers...

[[img]http://virtual.tehinterweb.net/livejournal/2010-03-26_raidperformance/thumbs/2010-03-26_ioscheduler_performance_log.png[/img]](http://virtual.tehinterweb.net/livejournal/2010-03-26_raidperformance/2010-03-26_ioscheduler_performance_log.png)

OK, here we are looking at the same graph as before, only this time on a logarithmic scale and limited to just a few contenders.

The first thing I want you to notice is the way the SSD almost completely inverts the shape of the 1TB drive using deadline - the SSD loves concurrency and takes a sharp performance hit every time we get to a single-process datapoint, whereas the conventional drive using deadline is just the opposite - a sharp peak with every single-process datapoint, followed by an immediate valley of the doldrums across 2, 3, 4, and 5 process datapoints.

Next, let's look at cfq and deadline more closely.  For small reads, deadline dominates - it dominated in the 16k portion that we didn't graph, and it's still dominating at 128k.  But once we get to 512k and up, the line for cfq basically looks like we're bridging across the peaks of the deadline graph.

Why do we care about this?  Well, cfq recently became the default I/O scheduler for the linux kernel, and to simplify things a little, there are two camps in a raging debate about it: the "cfq makes my computer horrible and laggy and slow" camp, and the "cfq outperforms deadline significantly" camp.

The "cfq is slow" camp has seen a server or workstation (ESPECIALLY workstations) completely stop responding to input for several seconds or more, sometimes long enough for critical processes to time out and things to stop working, when a really heavy I/O load got dumped on their machine.  When they switched to the deadline scheduler, they saw the problem go away, so they were happy.  "Deadline is better!"

The "cfq is better" camp tends to refer to studies from RedHat and elsewhere, which - much like this graph - show cfq outperforming deadline by a considerable margin.

So what's the deal?  Well, "Completely Fair Queuing" isn't really a very good name for cfq.  "Shut UP back there, you kids!" queuing might be closer to the case; cfq is "completely fair" in the same way a dad on his last nerve with a backseat of screaming kids is fair - it doesn't care about ANY of you as individuals anymore, it's just trying to get the car to Point B and get the heck OUT.  What cfq does is stack up a bunch of I/O requests, sort them out to try to match the ones that are close to each other together, and then execute them in the order that results in the most data going through the system per second.  As you can see from the graphs, it does just that.

The deadline scheduler works differently - as each I/O request comes into the kernel, this scheduler assigns a "deadline" for it to happen by.  If that deadline comes and goes and the I/O request is still unfulfilled, then that I/O request goes to the top of the heap and the kernel does its level best to fulfill that one before fulfilling any others.  This is the kind of scheduler you'd use for a "realtime" system, where latency is critical.

Now it's also worth noting that, since performance is the absolute worst at lower read/write sizes, when your computer is doing lots and lots of tiny reads and writes is most likely to be when you're NOTICING its performance.  Most people take high performance for granted very quickly, but they get irritated and pay attention to low performance every time it happens.  So, to those people, deadline is going to seem less annoying than cfq because they notice performance when it *drops*, not when it soars... and deadline does a better job than cfq across the board for small operations.

Add the better small-IO performance of deadline to cfq's tendency to put "whatever you just asked for" in the background for seconds at a time if that means a background process (like a large file copy, or a backup, or...) can go faster, and *now* you know why some people hate cfq no matter how many studies advocate it.

ZFS is pretty much in here just for reference.  From seat-of-the-pants experience, I can tell you that it's noticeably slower than ext4 under either scheduler, under most circumstances.  It seems less prone to the kind of "go away kid, I'm busy" that cfq tends to under heavy load, but it also doesn't "feel" anywhere near as "responsive" as deadline... just like the graph shows.  But, the major reason to use ZFS isn't performance, the major reason to use ZFS is a REALLY incredible feature set (data healing, dynamic pool configuration, per-directory quotas, snapshots... I could go on and on here) that would make far worse performance completely acceptable.  (It's also worth noting that ZFS has some really advanced caching algorithms that, if you have the RAM to make use of them, really go a long way towards camouflaging the low direct I/O performance you see here.)

---

### Post by jrssystemsnet on 2010-03-28
Oh, and some quick notes about partition alignment -

In the Linux tests, all partitions were aligned across 4K and 128K boundaries by changing the geometry to make "cylinders" align that way, as per [Ted Tso's blog post last year](http://thunk.org/tytso/blog/2009/02/20/aligning-filesystems-to-an-ssds-erase-block-size/).  (The WD drives and the SSD both use 4K physical sectors, and in the SSD's case, there is also a 128k "erase boundary" worth considering.)  The SSD was formatted with a sector size of 4k and stripe-width of 32, also as per Mr. Tso's post; the mdraid arrays were formatted with stripe-width and stride as calculcated by [this handy script here](http://uclibc.org/~aldot/mkfs_stride.html).

In the FreeBSD/ZFS tests, no alignment was done because, frankly, I spent quite a few hours messing with it and got tired of creating non-bootable partition tables; after a lot of Googling, I also came across some info claiming that ZFS used 512-byte sectors internally and there was no way to change that, so it wouldn't really help anyway.  So I gave up on it.  Mea culpa.

---

### Post by dragos2 on 2010-05-14
Good job. Can you please try to enable on-the-fly compression for ZFS and do a test with mixed data ? Some people claims that it improves throughout on certain loads.

---

### Post by jrssystemsnet on 2010-05-14
Sorry dragos, I don't have the test hardware lying around anymore. :)

I can tell you that enabling on-disk compression didn't have any "magic effects", though, because I did *play* with it - even doing writes from /dev/zero to a file on a pool with compression on isn't all that amazing; it does speed up, but not to a really incredible degree.

---

