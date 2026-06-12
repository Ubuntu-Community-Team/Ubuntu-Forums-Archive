---
title: "Software Raid 6 - Low throughput"
date: 2012-12-19
forum: Server Platforms
---

### Post by bothapn on 2012-12-19
Good day,

Summary: I'm experiencing a low throughput on Mysql (copy to tmp table takes ages) while the CPU usage is almost none at all where the tables are stored on a software raid device (/dev/md127) configuration 6 / dual parity. 

Detail:
It is an Ubuntu server running version 12 with Mysql 5.5. The Mysql tables are stored on a software raid device running as raid 6 (dual parity) across 4x 3TB Seagate desktop drives. The tables on mysql are somewhat big (1 database is about 1TB currently storing 2bil records). The server has 32G ram with 2x quad cores.

When I do intensive database operations which indicates to be disk bound operations such as copy-to-tmp-table, I don't see a high cpu usage, nor do I see high disk usage (iostat dump below). Though the load average on the server does go up to about 9.

I've tried allot of optimization using different sources from the internet, though it seems I'm missing something.

Can any one please assist me resolving the root cause ( I think it is the raid configuration that is wrong resulting in low throughput)?

Thanks allot!
  Pieter

I've pasted the configuration and log output I think might be relevant to this question below.

**IOStat - while doing the operations listed by mysql below:**
> Device:            tps    MB_read/s    MB_wrtn/s    MB_read    MB_wrtn
md127           193,00         4,19         4,98          8          9

Device:            tps    MB_read/s    MB_wrtn/s    MB_read    MB_wrtn
md127           109,00         4,58         3,06          9          6

Device:            tps    MB_read/s    MB_wrtn/s    MB_read    MB_wrtn
md127           170,50         5,23         7,07         10         14


**Mysql - show processlist**
> | 2227 | me| localhost       | tms      | Query      | 48108 | copy to tmp table               | ALTER TABLE ENGINE=INNODB                                                          |
| 2395 | me| localhost       | tms      | Query      | 51534 | copy to tmp table               | ALTER TABLE ENGINE=INNODB                                                              |
| 2451 | me| localhost       | tms      | Query      | 66657 | copy to tmp table               | ALTER TABLE ENGINE=INNODB                                                                |
| 3068 | me| localhost       | tms      | Query      | 40693 | Waiting for table flush         | INSERT INTO 
| 3071 | me| localhost       | NULL     | Query      | 40724 | Waiting for table flush         | FLUSH TABLES                                                                                         |
| 3505 | me| localhost       | tms      | Field List |  3215 | Waiting for table flush         |                                                                                                      |
| 3566 | me| localhost       | cc| Query      | 15900 | copy to tmp table               | ALTER TABLE a PARTITION by range (to_days(InsertDate))
| 3568 | me| localhost       | cc| Query      | 15856 | copy to tmp table               | ALTER TABLE b PARTITION by range (to_days(InsertDate))
| 3600 | me| localhost       | cc| Query      | 14086 | Waiting for table metadata lock | REPLACE INTO aVALUES ('4575652','110','2012-12-19','07:01:21','z9CSXPB2c/cn4ZBg+O |
| 6093 | me| localhost       | tms_n    | Query      |  4160 | NULL                            | LOAD DATA  LOCAL INFILE '/home/tms/imports/cxf.20121218.csv' IGNORE INTO TABLE `cxf_file` FIELD |
| 7376 | me| localhost       | tms      | Query      |  1312 | copy to tmp table               | ALTER TABLE `c` DROP INDEX `lMerchUSN_2`                                                           |
| 7777 | me| localhost       | tms      | Query      |   557 | Sorting result                  | SELECT  |


**/proc/mdstat**
> Personalities : [raid6] [raid5] [raid4] [linear] [multipath] [raid0] [raid1] [raid10]
md127 : active raid6 sdb1[3] sdd1[2] sdf1[0] sde1[1]
      5860530176 blocks super 1.2 level 6, 512k chunk, algorithm 2 [4/4] [UUUU]
      bitmap: 3/22 pages [12KB], 65536KB chunk


---

