---
title: "using bash to manage mysql"
date: 2017-02-13
forum: Server Platforms
---

### Post by Vegan on 2017-02-13
I have some CSV files with location information for IPv4 and IPv6 so I have manually made 2 separate tables.

```

LOAD DATA LOCAL
   INFILE 'IP2LOCATION-LITE-DB1.CSV'
INTO TABLE
   `ip2location_db1`
FIELDS TERMINATED BY ','
ENCLOSED BY '"'
LINES TERMINATED BY '\r\n'
IGNORE 0 LINES;

```

and 

```

LOAD DATA LOCAL
   INFILE 'IP2LOCATION-LITE-DB1.IPV6.CSV'
INTO TABLE
   `ip2location_db1_ipv6`
FIELDS TERMINATED BY ','
ENCLOSED BY '"'
LINES TERMINATED BY '\r\n'
IGNORE 0 LINES;

```

I guess I could can this into a SQL file and < from the file to mysql?

i was also interested in possibly updating the database or wholesale replace it?

I already have uploaded the CSV files to the server so that part is done, but I was then looking at leveraging the new database

By using a BASH script I was hoping to make updates easier?

---

