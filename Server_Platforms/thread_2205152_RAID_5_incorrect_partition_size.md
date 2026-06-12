---
title: "RAID 5 incorrect partition size"
date: 2014-02-12
forum: Server Platforms
---

### Post by Frankincense93 on 2014-02-12
Hi guys,

I recently added a new HDD to my RAID 5 setup, but the partition size is incorrect. The drives are all 1TB and there are 4 of them now. I followed this guide when making the array: [http://zackreed.me/articles/38-software-raid-5-in-debian-with-mdadm](http://zackreed.me/articles/38-software-raid-5-in-debian-with-mdadm)


mdadm --detail /dev/md0:
```
/dev/md0:        Version : 1.2
  Creation Time : Fri Nov 23 23:21:38 2012
     Raid Level : raid5
     Array Size : 2929890816 (2794.16 GiB 3000.21 GB)
  Used Dev Size : 976630272 (931.39 GiB 1000.07 GB)
   Raid Devices : 4
  Total Devices : 4
    Persistence : Superblock is persistent


    Update Time : Wed Feb 12 12:10:44 2014
          State : active
 Active Devices : 4
Working Devices : 4
 Failed Devices : 0
  Spare Devices : 0


         Layout : left-symmetric
     Chunk Size : 512K


           Name : SERVER:0  (local to host SERVER)
           UUID : d4038c21:1c919d42:6238b7dc:1c29a18a
         Events : 7477


    Number   Major   Minor   RaidDevice State
       4       8       17        0      active sync   /dev/sdb1
       1       8       49        1      active sync   /dev/sdd1
       3       8       33        2      active sync   /dev/sdc1
       5       8       65        3      active sync   /dev/sde1

```


fdisk -l:
```



WARNING: GPT (GUID Partition Table) detected on '/dev/sdb'! The util fdisk doesn't support GPT. Use GNU Parted.




Disk /dev/sdb: 1000.2 GB, 1000204886016 bytes
81 heads, 63 sectors/track, 382818 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000


   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1            2048  1953525167   976761560   83  Linux


WARNING: GPT (GUID Partition Table) detected on '/dev/sdc'! The util fdisk doesn't support GPT. Use GNU Parted.




Disk /dev/sdc: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000


   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1            2048  1953525167   976761560   83  Linux


WARNING: GPT (GUID Partition Table) detected on '/dev/sdd'! The util fdisk doesn't support GPT. Use GNU Parted.




Disk /dev/sdd: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000


   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1            2048  1953525167   976761560   83  Linux


Disk /dev/md0: 3000.2 GB, 3000208195584 bytes
2 heads, 4 sectors/track, 732472704 cylinders, total 5859781632 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 524288 bytes / 1572864 bytes
Disk identifier: 0x00000000


Disk /dev/md0 doesn't contain a valid partition table


WARNING: GPT (GUID Partition Table) detected on '/dev/sde'! The util fdisk doesn't support GPT. Use GNU Parted.




Disk /dev/sde: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x00000000


   Device Boot      Start         End      Blocks   Id  System
/dev/sde1            2048  1953525167   976761560   83  Linux



```

As you can see fdisk says the partition for md0 is invalid.


/proc/partitions
```
major minor  #blocks  name

   8        0  244198584 sda
   8        1     248832 sda1
   8        2          1 sda2
   8        5  243947520 sda5
   8       16  976762584 sdb
   8       17  976761560 sdb1
   8       32  976762584 sdc
   8       33  976761560 sdc1
   8       48  976762584 sdd
   8       49  976761560 sdd1
   9        0 2929890816 md0
 259        0 1953258496 md0p1
   8       64  976762584 sde
   8       65  976761560 sde1
 252        0  240164864 dm-0
 252        1    3776512 dm-1

```

So the array size for /dev/md0 is 2929890816, i.e. 3TB which is correct, but the partition /dev/md0p1 is only 1953258496.

When I run resize2fs /dev/md0p1:
```
resize2fs 1.42 (29-Nov-2011)
The filesystem is already 488314624 blocks long.  Nothing to do!

```

df -h shows the wrong size:
```
Filesystem               Size  Used Avail Use% Mounted on
/dev/mapper/SERVER-root  226G   11G  204G   5% /
udev                     1.8G  4.0K  1.8G   1% /dev
tmpfs                    712M  752K  711M   1% /run
none                     5.0M     0  5.0M   0% /run/lock
none                     1.8G     0  1.8G   0% /run/shm
/dev/sda1                228M   45M  171M  21% /boot
/dev/md0p1               1.8T  1.7T   18G 100% /media/RAID

```


I have tried everything I can think of, but I can't seem to get anywhere unfortunately. Suggestions? :) (and yes I do have a backup)

---

### Post by rubylaser on 2014-02-12
Hello, I see that you almost followed my tutorial to the letter :)  You should not have ended up with a partition on your array if you followed my tutorial exactly.  The filesystem should go right on top of the array.  Also, if you look at my tutorials fdisk -l will always say that the md device does not contain a valid partition table.  That's not a big deal.

Since your /dev/md0 device is the correct size, you just need to umount the array and resize the partition.
```

sudo -i
umount /media/RAID
fsck.ext4 /dev/md0p1
resize2fs /dev/md0p1
mount -a
```

That should expand your /dev/md0p1 partition to use all available space.  Let me know how that goes.

---

### Post by Frankincense93 on 2014-02-13
> **rubylaser said:**
> 
```

sudo -i
umount /media/RAID
fsck.ext4 /dev/md0p1
resize2fs /dev/md0p1
mount -a
```

Thanks for the reply! Great tutorial btw ;)


It seems fsck doesn't like the partition!

```
fsck.ext4 /dev/md0p1e2fsck 1.42 (29-Nov-2011)
fsck.ext4: No such file or directory while trying to open /dev/md0p1
Possibly non-existent device?

```

But, I can run it on the raid itself:
```
root@SERVER:~# fsck.ext4 /dev/md0
e2fsck 1.42 (29-Nov-2011)
```


/proc/partitions does not contain /dev/md0p1 and parted can't see it either

---

### Post by rubylaser on 2014-02-13
Well, that's different :)  Try to resize the filesystem on /dev/md0 then.

```

resize2fs /dev/md0

```

---

### Post by Frankincense93 on 2014-02-13
> **rubylaser said:**
> Well, that's different :)  Try to resize the filesystem on /dev/md0 then.

```

resize2fs /dev/md0

```


It seems like the array size is correct:
```
resize2fs 1.42 (29-Nov-2011)
The filesystem is already 732472704 blocks long.
```

And I did have a md0p1 partition before! I must have borked it :(,

So in order to restore the partition to how it should be, would your tutorial be a good start?

---

### Post by rubylaser on 2014-02-13
If you want to restore the partition, my tutorial is not a good place to start.  If you are planning on zeroing out the superblocks and starting over, it's a good place to start.

---

### Post by Frankincense93 on 2014-02-13
> **rubylaser said:**
> If you want to restore the partition, my tutorial is not a good place to start.  If you are planning on zeroing out the superblocks and starting over, it's a good place to start.

Ok fair enough, is it possible to restore a partition without destroying the data?

---

### Post by rubylaser on 2014-02-13
It's hard to give advice unless you know exactly what you did to the partition.  Unfortunately in most cases you are going to want to restore from backup if you have one, otherwise, you are going to need to use something like [testdisk]("https://apps.ubuntu.com/cat/applications/precise/testdisk/") to salvage the files, but this restores them as unnamed, un-foldered files (a last resort).  Do you happen to know what commands you ran?  Maybe provide the output of history as root.

```
history
sudo history

```

---

### Post by Frankincense93 on 2014-02-14
> **rubylaser said:**
> It's hard to give advice unless you know exactly what you did to the partition.  Unfortunately in most cases you are going to want to restore from backup if you have one, otherwise, you are going to need to use something like [testdisk]("https://apps.ubuntu.com/cat/applications/precise/testdisk/") to salvage the files, but this restores them as unnamed, un-foldered files (a last resort).  Do you happen to know what commands you ran?  Maybe provide the output of history as root.

```
history
sudo history

```


Good idea:
I will just post all my recent history but I imagine it'll be this vain hope of fixing everything that ruined it:
```
 1929  mkfs.ext4 /dev/md0 1930  sudo mkfs.ext4 /dev/md0
 1931  sudo mkfs.ext4 -b 4096 -E stride=128,stripe-width=384 /dev/md0
 1932  tune2fs -m 0 /dev/md0
 1933  sudo tune2fs -m 0 /dev/md0
 1934  sudo mdadm --detail /dev/md0
```


I really should ask for help before destroying everything :(


Here is the whole lot:
```
 1821  sudo sgdisk -R=/dev/sde /dev/sdd 1822  sgdisk --backup=table /dev/sdb
 1823  sudo sgdisk --backup=table /dev/sdb
 1824  tail -n 10 /var/log/syslog
 1825  sudo sgdisk --backup=table /dev/sdb
 1826  tail -n 10 /var/log/syslog
 1827  sfdisk -d /dev/sdd > part_table
 1828  sudo sfdisk -d /dev/sdd > part_table
 1829  ls
 1830  sudo sfdisk -d /dev/sde < part_table
 1831  sgdisk -R=/dev/sdd /dev/sde
 1832  sudo sgdisk -R=/dev/sdd /dev/sde
 1833  sudo sgdisk -R=/dev/sdd /dev/sdc
 1834  sudo fdisk -l
 1835  sgdisk --replicate=/dev/sdc /dev/sdd
 1836  sudo sgdisk --replicate=/dev/sdc /dev/sdd
 1837  sudo sgdisk --replicate=/dev/sdc /dev/sdb
 1838  parted /dev/sdc
 1839  sudp parted /dev/sdc
 1840  sudo parted /dev/sdc
 1841  sudo parted /dev/sdd
 1842  sudo parted /dev/sde
 1843  nano /etc/initramfs-tools/conf.d/mdadm
 1844  update-initramds -u
 1845  update-initramfs -u
 1846  sudo update-initramfs -u
 1847  sudo shutdown -r now
 1848  sudo mdadm --start /dev/md0
 1849  sudo mdadm --assemble /dev/md0
 1850  sudo mdadm --detail /dev/md0
 1851  sudo parted /dev/sdb
 1852  sudo parted /dev/sdc
 1853  sudo parted /dev/sdd
 1854  sudo mdadm --stop /dev/md0
 1855  sudo mdadm --assemble /dev/md0
 1856  sudo mdadm --stop /dev/md0
 1857  sudo fdisk -l
 1858  su
 1859  sudo fdisk -l
 1860  su
 1861  cd /
 1862  sudo mdadm --assemble /dev/md0
 1863  sudo mdadm --stop /dev/md0
 1864  sudo mdadm --assemble /dev/md0
 1865  sudo mdadm --detail /dev/md0
 1866  sudo mdadm --stop /dev/md0
 1867  sudo umount /dev/md0p1
 1868  sudo mdadm --stop /dev/md0
 1869  su
 1870  sudo mdadm --assemble /dev/md0
 1871  tail /var/log/syslog
 1872  sudo parted /dev/sde
 1873  sudo mdadm --remove /dev/md0
 1874  sudo mdadm --remove /dev/md0 /dev/sde
 1875  sudo mdadm --detail /dev/md0
 1876  sudo mdadm --manage /dev/md0 --fail /dev/sde1
 1877  sudo mdadm --remove /dev/md0 /dev/sde
 1878  sudo mdadm --remove /dev/md0 /dev/sde1
 1879  sudo mdadm --manage /dev/md0 --remove /dev/sde1
 1880  sudo mdadm --manage /dev/md0 --add /dev/sde1
 1881  watch /proc/mdstat
 1882  sudo watch /proc/mdstat
 1883  cat /proc/mdstat
 1884  disable shutdown
 1885  disableshutdown
 1886  cat /proc/mdstat
 1887  cd /
 1888  sudo mdadm --detail /dev/md0
 1889  df -h
 1890  sudo fdisk -l
 1891  sudo resize2ef
 1892  sudo resize
 1893  sudo resize2fs /dev/md0p1
 1894  sudo smartctl -a /dev/sdb
 1895  sudo mdadm --assemble /dev/md0-
 1896  sudo mdadm --assemble /dev/md0
 1897  sudo mdadm detailassemble /dev/md0
 1898  sudo mdadm --detail /dev/md0
 1899  sudo shutdown -r now
 1900  sudo resize2fs /dev/md0
 1901  sudo resize2fs /dev/md0p1
 1902  cd /
 1903  df -h
 1904  sudo fdisk -l
 1905  view /proc/partitions
 1906  nano /etc/fstab
 1907  sudo mdadm --grow /dev/md0 --raid-devices=4
 1908  sudo e2fsck -f /dev/md0
 1909  sudo e2fsck -f /dev/md0p1
 1910  sudo umount /dev/md0p1
 1911  sudo e2fsck -f /dev/md0p1
 1912  sudo mount -a
 1913  cd /media/RAID
 1914  ls
 1915  cksfv -r -q
 1916  sudo umount /dev/md0p1
 1917  cd /
 1918  sudo umount /dev/md0p1
 1919  sudo resize2fs -p /dev/md0p1
 1920  sudo e2fsck -f /dev/md0p1
 1921  sudo resize2fs /dev/md0p1 3TB
 1922  sudo mdadm --detail /dev/md0
 1923  sudo parted -l
 1924  sudo fdisk -l
 1925  view /proc/partitions
 1926  sudo parted -l
 1927  sudo resize2fs /dev/md0p1
 1928  sudo parted /dev/md0p1
 1929  mkfs.ext4 /dev/md0
 1930  sudo mkfs.ext4 /dev/md0
 1931  sudo mkfs.ext4 -b 4096 -E stride=128,stripe-width=384 /dev/md0
 1932  tune2fs -m 0 /dev/md0
 1933  sudo tune2fs -m 0 /dev/md0
 1934  sudo mdadm --detail /dev/md0
 1935  sudo fdisk -l
 1936  sudo mount -a
 1937  tail /var/log/syslog
 1938  sudo mount -a
 1939  tail /var/log/syslog
 1940  sudo parted -l
 1941  view /proc/partitions
 1942  sudo mount -a
 1943  sudo fdisk -l
 1944  sudo e2fsck -f /dev/md0p1
 1945  y
 1946  sudo e2fsck -f /dev/md0p1
 1947  sudo fdisk -l
 1948  sudo parted -l
 1949  sudo mdadm --detail /dev/md0
 1950  view /proc/partitions
 1951  sudo mount -a
 1952  cd /media/RAID
 1953  ls
 1954  df -h
 1955  cd /
 1956  ls
 1957  sudo mdadm --detail /dev/md0
 1958  sudo resize2fs /dev/md0p1
 1959  sudo parted /dev/md0p1
 1960  sudo parted -l
 1961  sudo parted /dev/md0
 1962  sudo mdadm --detail /dev/md0
 1963  sudo fdisk -l
 1964  sudo fsck /dev/md0
 1965  sudo fsck /dev/md0p1
 1966  view /proc/partitions
 1967  sudo resize2fs /dev/md0
 1968  sudo resize2fs /dev/md0p1
 1969  sudo mdadm --examine /dev/sde
 1970  sudo mdadm --examine /dev/sdd
 1971  sudo mdadm --examine /dev/sdb
 1972  df -h
 1973  sudo parted -l
 1974  sudo parted /dev/md0p1
 1975  sudo umount /dev/md0p1
 1976  sudo e2fsck /dev/md0p1
 1977  sudo fsck /dev/md0p1
 1978  sudo mount -a
 1979  tail /var/log/syslog
 1980  sudo parted /dev/md0p1
 1981  cd /
 1982  sudo -i
 1983  cd /
 1984  sudo mdadm --detail /dev/md0
 1985  nano /proc/partitions
 1986  sudo parted /dev/md0
 1987  sudo parted -l
 1988  sudo parted /dev/md0
 1989  sudo parted /dev/md0p1
 1990  sudo parted /dev/md0
 1991  sudo shutdown -r now
 1992  sudo nano /proc/partitions
 1993  cd /media/RAID
 1994  ls
 1995  cd /
 1996  gpart /dev/md0
 1997  sudo gpart /dev/md0
 1998  history

```

---

### Post by rubylaser on 2014-02-14
Yeah, there's nothing there other than the initial creation of the partitions on the disks and alot of calls to mkfs.ext4 on the raid array :)

---

### Post by Frankincense93 on 2014-02-14
> **rubylaser said:**
> Yeah, there's nothing there other than the initial creation of the partitions on the disks and alot of calls to mkfs.ext4 on the raid array :)

Here is the history for root:
```
 1777  chkdsk 1778  fdisk -k
 1779  fdisk -l
 1780  sudo shutdown -r now
 1781  watch /proc/mdstat
 1782  cd /
 1783  exit
 1784  watch /proc/mdstat
 1785  su root
 1786  cd /
 1787  exit
 1788  watch /proc/mdstat
 1789  sudo watch /proc/mdstat
 1790  cd  /
 1791  watch cat /proc/mdstat
 1792  cat /proc/mdstat
 1793  mdadmc /dev/md0
 1794  mdadmc -s /dev/md0
 1795  mdadm -s /dev/md0
 1796  mdadm --help
 1797  mdadm --help-options
 1798  mdadm /dev/md0 -D
 1799  mdadm -D /dev/md0
 1800  fdisk -l
 1801  smartmon
 1802  smartmontools
 1803  smart
 1804  smartmon
 1805  smartctl
 1806  smartctl -h
 1807  smartctl /dev/sdb -a
 1808  smartctl -h
 1809  smartctl /dev/sdb -H
 1810  smartctl /dev/sdb -t
 1811  smartctl /dev/sdb -t=long
 1812  smartctl /dev/sdb -t long
 1813  smartctl /dev/sdb -X
 1814  smartctl /dev/sdb -t short
 1815  smartctl /dev/sdb -t
 1816  smartctl /dev/sdb
 1817  smartctl /dev/sdb -a
 1818  mdadm --help
 1819  mdadm --assemble /dev/md90
 1820  mdadm --assemble /dev/md0
 1821  mdadm --manage /dev/md0
 1822  mdadm --help-options
 1823  mdadm /dev/md0
 1824  mdadm /dev/md0 -d
 1825  mdadm /dev/md0 --detail
 1826  mdadm --detail /dev/md0
 1827  mdadm --stop /dev/md0
 1828  mdadm --examine /dev/md0
 1829  mdadm --assemble /dev/md0
 1830  mdadm --manage --re-add /dev/md0 /dev/sdb
 1831  mdadm --manage --re-add /dev/md0 /dev/sdb1
 1832  cat /proc/mdstat
 1833  mdadm -a /dev/md0 /dev/sdb1
 1834  cat /proc/mdstat
 1835  watch /proc/mdstat
 1836  cat /proc/mdstat
 1837  watch /proc/mdstat
 1838  sudo watch /proc/mdstat
 1839  su watch /proc/mdstat
 1840  su root watch /proc/mdstat
 1841  su root
 1842  echo 25000 > /proc/sys/dev/raid/speed_limit_min
 1843  cd /
 1844  exit
 1845  watch /proc/mdstat
 1846  exity
 1847  exit
 1848  watch /proc/mdstat
 1849  exit
 1850  fdisk -l
 1851  fsck /dev/sde
 1852  parted /dev/sde
 1853  fsck /dev/sde
 1854  e2fsck /dev/sde
 1855  e2fsck --help /dev/sde
 1856  fsck --help /dev/sde
 1857  fdisk /dev/sde
 1858  sudo mdadm --add /dev/md0 /dev/sde1
 1859  mdadm
 1860  mdadm --help
 1861  mdadm --examine /dev/md0
 1862  mdadm --detail /dev/md0
 1863  mdadm --assemble /dev/md0
 1864  mdadm /dev/md0
 1865  mdadm --detail /dev/md0
 1866  mdadm /dev/md0 --manage
 1867  mdadm --assemble /dev/md0 /dev/sd[bcd]1
 1868  mdadm --assemble-scan /dev/md0
 1869  mdadm --assemble-scan
 1870  mdadm --assemble--scan /dev/md0
 1871  mdadm --assemble--scan
 1872  mdadm --assemble --scan
 1873  mdadm --detail /dev/md0
 1874  mdadm --remove /dev/md0 /dev/sde
 1875  mdadm --zero-superblock /dev/sde1
 1876  mdadm --examine /dev/sde1
 1877  mdadm --examine /dev/sde
 1878  mdadm --examine /dev/md0
 1879  mdadm --manage /dev/md0 --add /dev/sde1
 1880  cat /etc/mdadm/mdadm.conf
 1881  /etc/init.d/mdadm-raid start
 1882  nano /etc/mdadm/mdadm.conf
 1883  nano /proc/partitions
 1884  fdisk /dev/sde
 1885  n
 1886  fdisk /dev/sde
 1887  fdisk -l
 1888  nano /etc/mdadm/mdadm.conf
 1889  mdadm --assemble /dev/md0
 1890  tail syslog
 1891  syslog
 1892  cd var
 1893  cd log
 1894  tail syslog
 1895  cd /media
 1896  ls RAID
 1897  cd /
 1898  mdadm --add /dev/md0 /dev/sde1
 1899  mdadm --detail /dev/md0
 1900  nano /etc/mdadm/mdadm.conf
 1901  mdadm --detail /dev/md0
 1902  e2fsck -f /dev/md0
 1903  umount /dev/md0
 1904  umount /dev/md0p1
 1905  e2fsck -f /dev/md0
 1906  sudo resize2fs /dev/md0
 1907  sudo resize2fs /dev/md0p1
 1908  sudo shutdown -r now
 1909  mdadm --detail /dev/md0
 1910  tail /var/log/syslog
 1911  tail -n 20 /var/log/syslog
 1912  e2fsck -f /dev/md0p1
 1913  umount /dev/md0p1
 1914  e2fsck -f /dev/md0
 1915  e2fsck -f /dev/md0p1
 1916  sudo resize2fs /dev/md0p1
 1917  sudo mdadm --add /dev/md0 /dev/sde1
 1918  sudo fdisk -l
 1919  sudo mdadm --remove /dev/md0 /dev/sde1
 1920  mdadm --stop /dev/md0
 1921  sudo mdadm --assemble /dev/md0
 1922  sudo resize2fs /dev/md0p1
 1923  cat /proc/mdstat
 1924  fdisk -l
 1925  mount /dev/md0p1 /media/RAID
 1926  cd /media/RAID
 1927  ls
 1928  df -h
 1929  df -h /
 1930  df -h .
 1931  cd /
 1932  mdadm -D /dev/md0 | grep -e "Array Size" -e "Device Size"
 1933  mdadm -D /dev/md0 | grep -e "Device Size"
 1934  mdadm -D /dev/md0 | grep -e "Array Size" -e "Device Size"
 1935  mdadm --grow /dev/md0 -z max
 1936  mdadm --grow /dev/md0 -z max --assume-clean
 1937  mdadm -D /dev/md0 | grep -e "Array Size" -e "Device Size"
 1938  resize2fs /dev/md0
 1939  umount /dev/md0
 1940  umount /dev/md0p1
 1941  resize2fs /dev/md0
 1942  resize2fs /dev/md0p1
 1943  fdisk -l
 1944  cat /proc/mdstat
 1945  mdadm -A --scan
 1946  mdadm --grow /dev/md0 --size=max
 1947  resize2fs /dev/md0
 1948  resize2fs /dev/md0p1
 1949  e2fsck -f /dev/md0
 1950  e2fsck -f /dev/md0p1
 1951  mdadm --detail /dev/md0
 1952  nano /etc/mdadm/mdadm.conf
 1953  mdadm --examine /dev/sde1
 1954  umount /dev/md0p1
 1955  resize2fs
 1956  resize2fs /dev/md0p1
 1957  mdadm --detail /dev/md0
 1958  resize2fs -S 512 -p /dev/md0p1 3000GB
 1959  resize2fs -S 512 -p /dev/md0p1 3TB
 1960  resize2fs -S 512 -p /dev/md0p1 max
 1961  resize2fs -S 512 -p /dev/md0p1 --size=max
 1962  resize2fs -S 512 -p /dev/md0p1 max
 1963  fsck /dev/md0
 1964  fsck /dev/md0p1
 1965  resize2fs /dev/md0
 1966  resize2fs /dev/md0p1
 1967  mdadm --detail /dev/md0
 1968  sudo shutdown -r now
 1969  sfdisk -d /dev/sdb | sfdisk /dev/sdc
 1970  sfdisk -d /dev/sdc | sfdisk /dev/sdd
 1971  exit
 1972  sfdisk -d /dev/sdd | sfdisk /dev/sde
 1973  cd /
 1974  exit
 1975  fdisk -l
 1976  exit
 1977  umount /media/RAID
 1978  fsck.ext4 /dev/md0p1
 1979  mdadm --assemblr /dev/md0
 1980  mdadm --assemble /dev/md0
 1981  umount /media/RAID
 1982  fsck.ext4 /dev/md0p1
 1983  mdadm --detail /dev/md0
 1984  fsck.ext4 /dev/md0p1
 1985  fsck.ext4 /dev/md0
 1986  view /proc/partitions
 1987  parted -l
 1988  parted /dev/md0
 1989  parted /dev/md0p1
 1990  sudo fdisk -l
 1991  parted /dev/md0p1
 1992  resize2fs /dev/md0
 1993  parted -l
 1994  parted /dev/md0
 1995  gpart /dev/md0
 1996  sudo apt-get instlal gpart
 1997  sudo apt-get install gpart
 1998  gpart /dev/md0
 1999  history

```

---

### Post by Frankincense93 on 2014-02-17
For anyone look at this in the future. I ended up re-creating the partition ([http://zackreed.me/articles/38-software-raid-5-in-debian-with-mdadm](http://zackreed.me/articles/38-software-raid-5-in-debian-with-mdadm)) on /dev/md0 and restored data from a backup.

---

