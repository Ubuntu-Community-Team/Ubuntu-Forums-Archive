---
title: "GlusterFS: Severe performance problem with concurrent HTTP requests"
date: 2011-11-15
forum: Server Platforms
---

### Post by fredkin on 2011-11-15
Hi Guys,


  We have been using GlusterFS version 2.08 for a couple of years with good results until a few weeks ago. Our problems started occurring when the concurrent traffic to our PHP site increased to about 200 concurrent users on each front end server. At this point the performance of the site was so bad that page requests would just time out and the users would be unable to use the system. Our system has the following characteristics:
   
  - Load Balancer.
   
  - Two front end machines with Xeon Quad Core X3360 2.83 GHz, 4 GB of RAM and disks of 7200 RPMs in RAID 1 configuration. Each of these machines are running apache servers and we were using GlusterFS which is installed in both of the front end machines and was used to maintain the files submitted by the users as well as the website code and  its contents (PHP, images, css, js, html) synchronized between these two machines.
   
  - Database server with 2x Xeon Quad Core E5410 2.33 GHz, 8 GB of RAM and disks of 10 k RPMs in RAID 10 configuration. This server is running an Oracle database.
   
   
  In order to replicate the problem faced by the users I used apache’s ab tool to simulate 200 concurrent requests against one of the front end servers and using top and iostat I saw that the io wait time went to the roof and that GlusterFS was using 30-40% of the server’s CPU. Once 200 concurrent requests were being made to the server it became unable to serve php webpages because the user would need to wait forever to get each page to the point where web pages would time out.
   
  Based on these results I disabled GlusterFS and now each server is able to serve over 400 concurrent requests at a time (I haven’t test it using more requests but I am pretty sure it wouldn’t have any problem serving them). However, based on what I have read about GlusterFS being able to handle cloud infrastructures that contain petabytes of data, I am pretty sure that I must be missing something.
   
  Can you please help me with this?
   
  Thanks and Regards,
  Fred

---

