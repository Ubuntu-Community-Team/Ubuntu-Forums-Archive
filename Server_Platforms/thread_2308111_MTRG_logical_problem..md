---
title: "MTRG logical problem."
date: 2015-12-31
forum: Server Platforms
---

### Post by gardenair on 2015-12-31
I have configured MRTG . Things are working ok but I am facing logical problem in MRTG graph.I plot "/" , " /var"  ,my created partition  "/mnt/pdc-share" and "/mnt/tic-share".

The issue is when I copy a large file (like 450Mb) in the drive  /mnt/pdc-share the system also plot the graph on same time on  /mnt/tic-share  which is wrong because i am working on the /mnt/pdc-share drive not /mnt/tic-share drive.

My second issue is I shutdown the server at 5pm ,In morning Time when I run MRTG it show me graph of "Available Memory" ,Free Memory and "/" i.e root partition as it also  worked at night .Where as I completely off my server at 5:00 Pm. Please let me know why it not refresh the graph from Morning Time 9:00 AM.

```
[FONT=arial][SIZE=5]
[/SIZE][/FONT]#Root partition Target[Est_Master-root]: dskAvail.1&dskTotal.1:public@localhost
Title[Est_Master-root]: Disk usage: Root partition on Est_Master
PageTop[Est_Master-root]:<H1> Disk usage: Root partition on Est_Master (/)</H1>
MaxBytes[Est_Master-root]: 8217464832
Options[Est_Master-root]: nopercent,gauge,noinfo,growright
LegendI[Est_Master-root]:  Available:
LegendO[Est_Master-root]:  Total:
Ylegend[Est_Master-root]: bytes
ShortLegend[Est_Master-root]: bytes
Legend1[Est_Master-root]: Total space
Legend2[Est_Master-root]: Available space
Legend3[Est_Master-root]: Maximum total space
Legend4[Est_Master-root]: Maximum available space
kMG[Est_Master-root] : k,M,G,T,P,X
#Unscaled[Est_Master-root]: dwmy
#Directory[Est_Master-root]: system


# /var partition
Target[Est_Master-var]: dskAvail.1&dskTotal.1:public@localhost
Title[Est_Master-var]: Disk usage: /var partition on Est_Master
PageTop[Est_Master-var]:<H1> Disk usage: PDC partition on Est_Master (/var)</H1>
MaxBytes[Est_Master-var]: 8217464832
Options[Est_Master-var]: nopercent,gauge,noinfo,growright
LegendI[Est_Master-var]:  Available:
LegendO[Est_Master-var]:  Total:
Ylegend[Est_Master-var]: bytes
ShortLegend[Est_Master-var]: bytes
Legend1[Est_Master-var]: Total space
Legend2[Est_Master-var]: Available space
Legend3[Est_Master-var]: Maximum total space
Legend4[Est_Master-var]: Maximum available space
kMG[Est_Master-var] : k,M,G,T,P,X




# /mnt/pddc-share partition availablity  -7
Target[Est_Master-pdc]: dskAvail.1&dskTotal.1:public@localhost
Title[Est_Master-pdc]: Disk usage: /mnt/pdc-share  partition on Est_Master
PageTop[Est_Master-pdc]:<H1> Disk usage: pdc partition on Est_Master (/mnt/pdc-share)</H1>
MaxBytes[Est_Master-pdc]: 8217464832
Options[Est_Master-pdc]: nopercent,gauge,noinfo,growright
LegendI[Est_Master-pdc]:  Available:
LegendO[Est_Master-pdc]:  Total:
Ylegend[Est_Master-pdc]: bytes
ShortLegend[Est_Master-pdc]: bytes
Legend1[Est_Master-pdc]: Total space
Legend2[Est_Master-pdc]: Available space
Legend3[Est_Master-pdc]: Maximum total space
Legend4[Est_Master-pdc]: Maximum available space
kMG[Est_Master-pdc] : k,M,G,T,P,X




# /mnt/tic-share  partition availability -8
Target[Est_Master-tic]: dskAvail.1&dskTotal.1:public@localhost
Title[Est_Master-tic]: Disk usage: /mnt/tic-share  partition on Est_Master-tic
PageTop[Est_Master-tic]:<H1> Disk usage: TIC partition on Est_Master-tic (/mnt/tic-share)</H1>
MaxBytes[Est_Master-tic]: 8217464832
Options[Est_Master-tic]: nopercent,gauge,noinfo,growright
LegendI[Est_Master-tic]:  Available:
LegendO[Est_Master-tic]:  Total:
Ylegend[Est_Master-tic]: bytes
ShortLegend[Est_Master-tic]: bytes
Legend1[Est_Master-tic]: Total space
Legend2[Est_Master-tic]: Available space
Legend3[Est_Master-tic]: Maximum total space
Legend4[Est_Master-tic]: Maximum available space
kMG[Est_Master-tic] : k,M,G,T,P,X



```

Thanks ,

---

