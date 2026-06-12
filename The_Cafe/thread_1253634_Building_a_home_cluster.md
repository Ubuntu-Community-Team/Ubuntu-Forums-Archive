---
title: "Building a home cluster"
date: 2009-08-30
forum: The Cafe
---

### Post by hwttdz on 2009-08-30
I'm thinking about building a home cluster, probably start with core2quads and expand with i7's once the cost per computing power of the i7 falls some (and the boards get cheaper).  I was thinking something along the threaded rod setup.  The issue of maintenance would not be so much because if I only have 5 nodes or so the worst that could happen would be I would have to remove 3 boards.  My biggest concerns at this point are some sort of enclosure and heat sinks on the cpus.  I have good experience with zalmans in normal machines, but those require up to 160 mm vertical clearance, which would prevent stacking the boards closer than that.  Zalman makes a blow down cooler, which requires about 70 mm vertical clearance, I have found some super low profile coolers (dynatron), but the noise output of those is exceptionally high and the capacity is only 130 watts (right at the point of these processors).  Anybody have any advice about casing/cooling? Or given any thought/tried a cluster of their own?

---

### Post by racerraul on 2009-08-30
> **hwttdz said:**
> I'm thinking about building a home cluster, probably start with core2quads and expand with i7's once the cost per computing power of the i7 falls some (and the boards get cheaper).  I was thinking something along the threaded rod setup.  The issue of maintenance would not be so much because if I only have 5 nodes or so the worst that could happen would be I would have to remove 3 boards.  My biggest concerns at this point are some sort of enclosure and heat sinks on the cpus.  I have good experience with zalmans in normal machines, but those require up to 160 mm vertical clearance, which would prevent stacking the boards closer than that.  Zalman makes a blow down cooler, which requires about 70 mm vertical clearance, I have found some super low profile coolers (dynatron), but the noise output of those is exceptionally high and the capacity is only 130 watts (right at the point of these processors).  Anybody have any advice about casing/cooling? Or given any thought/tried a cluster of their own?

I support tons of these at work (all Windows DB clusters)

Are you sharing any type of remote storage?  Sounds like a very expensive project, what are you going to use it for?

If you are just experimenting, I'd see if you can Cluster VM sessions in a single physical host.

---

### Post by hwttdz on 2009-08-30
What do you mean sharing remote storage?

I'd be using it for molecular mechanics simulations.  

A fast ssd on every node would be great, but that would be at least $120 (I wish I could get 8gb ssd's instead of 32g ssd's) and that's pretty steep. I think I'll be able to test by adding my home machine as a node to my work machine.  Perhaps I was unclear, internode communication doesn't need to be fast, I essentially hand out jobs to processors and they never talk to each other again. I have a sge queue set up on my machine right now, but only one node, 4 slots.

---

### Post by hwttdz on 2009-08-30
pjess60, I think you overestimate what I'm talking about here.  I'm probably looking at an average power draw per added board of maybe 50 W when at full load.  So all told I'll be at desktop + (nodes-1)*50 usage.  And since I'm starting with 2-3 nodes, I'll be using about 50-100 watts more than a conventional desktop.  The efficiencies of scale don't pan out.

---

### Post by aikiwolfie on 2009-08-30
Have you looked into liquid cooling or maybe a hybrid fan assited liquid cooling solution?

---

