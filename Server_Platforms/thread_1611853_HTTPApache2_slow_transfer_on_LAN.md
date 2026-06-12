---
title: "HTTP/Apache2 slow transfer on LAN"
date: 2010-11-02
forum: Server Platforms
---

### Post by Belac_K on 2010-11-02
I work in an environment where we test and repair over a hundred laptops/desktops a day.  I use a mix of gPXE and Apache/PHP to generate and serve various boot images to the mahcines.  

My problem arises from the fact that while some boot images are quite small (3-4 MB), others are large (200 MB).  While transferring these large images (via HTTP by gPXE) my max transfer speed barely tops 2 MByte/Sec (16 MBits/Sec Correct?) outbound on the server.  This can mean a fairly long wait for the Test Machine.  Since this all takes place on a LAN environment, even a 200 MB file transfer should not take that long.  Using iperf, I can acheivement transfer rates of up to  9MBytes/Sec (72 Mbits/Sec), so it doesn't seem like a hardware issue.

Is there something limiting what Apache2 transfers, or somthing else capping the file transfers?  It gets pretty frustating waiting upwards of 5 minutes for a 200MB transfer.  Any help would be appreciated.

---

