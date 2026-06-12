---
title: "Rsync fails to abort. Copying files from USB attached HDD to a ZFS file server."
date: 2014-12-21
forum: Server Platforms
---

### Post by RGee89 on 2014-12-21
I'm trying to rsync about 400GB of data from a USB attached SATA drive to a ZFS pool. 
So what I see is 15MB/s reads from the USB which I think is expected given the external HDD dock isn't USB 3.0. 
I tried to abort the rsync while it was in progress by hitting <CTRL>+C. 
It reported a "Broken Pipe" and I see the rsync command in the background when I issue the command: ```
ps -aux | grep rsync
```

Below is the iostat output after I had tried to abort the rsync command. Does this look right?

```
user@FileServer:~&#10219; sudo iostat -dmx
Linux 3.13.0-39-generic (FileServer)       12/21/2014      _x86_64_        (32 CPU)


Device:         rrqm/s   wrqm/s     r/s     w/s    rMB/s    wMB/s avgrq-sz avgqu-sz   await r_await w_await  svctm  %util
sda               0.66     1.05    5.66    1.27     0.16     0.06    64.70     0.01    0.78    0.54    1.89   0.15   0.11
sdb               0.47     1.94    7.73   36.33     0.35     2.84   148.18     2.94   66.66   76.35   64.60  13.11  57.77
sdc               0.48     1.94    7.69   36.27     0.35     2.84   148.48     3.09   70.20   77.88   68.57  13.39  58.88
sdd               0.47     1.93    7.74   36.31     0.35     2.84   148.27     3.15   71.44   78.94   69.84  13.46  59.28
sde               0.47     1.92    7.74   36.28     0.35     2.84   148.29     3.15   71.40   78.22   69.94  13.50  59.42
sdf               0.46     2.03    7.70   36.35     0.35     2.84   148.30     1.08   24.46   57.89   17.38   7.85  34.58
sdh               0.39     2.01    7.70   36.29     0.35     2.84   148.49     1.13   25.66   58.78   18.63   7.94  34.91
sdg               0.53     2.43    7.47   35.79     0.35     2.84   151.04     1.33   30.62   80.41   20.23   8.59  37.18
sdi               0.38     2.03    7.72   36.23     0.35     2.84   148.64     1.07   24.36   57.88   17.21   7.86  34.55
sdj            3768.55     0.51  250.49    0.16    15.67     0.00   128.02     1.32    5.27    5.24   44.79   1.90  47.57



```

Thanks for the help!

---

### Post by nerdtron on 2014-12-21
> It reported a "Broken Pipe" and I see the rsync command in the background when I issue the command:

That command should terminate rsync. And you just provided "ps aux | grep rsync" ---> what is the output of this command?

---

