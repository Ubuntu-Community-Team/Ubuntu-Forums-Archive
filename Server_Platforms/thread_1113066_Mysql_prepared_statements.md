---
title: "Mysql prepared statements"
date: 2009-04-01
forum: Server Platforms
---

### Post by PeterK2003 on 2009-04-01
I setup a mysql server which seems to be working fine except when i try to execute prepared statements.

The line(php) that it chokes on is: ```
$this->connection->prepare($SQL);
```

It doesn't seem to do anything--no errors even--it just seems to return an empty string.  I know the code is correct b/c if i point it at my win/mysql server it works fine.  

Do i need to enable prepared statements in mySQL somewhere?  Oh and my non-prepared queries work fine.

Thanks,
~Peter

---

### Post by PeterK2003 on 2009-04-03
Bump

---

### Post by PeterK2003 on 2009-04-14
Bump

---

### Post by dsauxier on 2009-04-16
See these instructions on using PREPARE, EXECUTE, and DEALLOCATE PREPARE : 
[http://dev.mysql.com/tech-resources/articles/4.1/prepared-statements.html](http://dev.mysql.com/tech-resources/articles/4.1/prepared-statements.html)

---

### Post by PeterK2003 on 2009-04-16
```
PREPARE stmt_name FROM "select * from observations where date = ?";# MySQL returned an empty result set (i.e. zero rows).
SET @test_parm = "2009-04-14 08:01:00";# MySQL returned an empty result set (i.e. zero rows).
EXECUTE stmt_name USING @test_parm ;# Rows: 1
```

That seemed to work so what could be wrong?  I ran it from Phpmyadmin which is on the same web server.  Weird!

---

### Post by PeterK2003 on 2009-04-21
ok it seems that it is mainly one query that is failing

```
$SQL = "select MAX(TEMPERATURE), MAX(HUMIDITY), MAX(DEWPOINT), MAX(HEAT_INDEX), MAX(GUST_SPEED), MAX(WIND_SPEED), ".
	"MAX(BAROMETER), MAX(RAIN_RATE), MAX(INDOOR_TEMPERATURE), MAX(INDOOR_HUMIDITY), MIN(TEMPERATURE), MIN(HUMIDITY), ".
	"MIN(DEWPOINT), MIN(WINDCHILL), MIN(BAROMETER), MIN(INDOOR_TEMPERATURE), MIN(INDOOR_HUMIDITY), ".
	"(select MAX(DATE) FROM OBSERVATIONS WHERE TEMPERATURE = (Select MAX(TEMPERATURE) from observations where date between ? and ?) and date between ? and ?) MAXTEMPTIME ".
	", (select MAX(DATE) FROM OBSERVATIONS WHERE HUMIDITY = (Select MAX(HUMIDITY) from observations where date between ? and ?) and date between ? and ?) MAXHUMTIME ".
	", (select MAX(DATE) FROM OBSERVATIONS WHERE DEWPOINT = (Select MAX(DEWPOINT) from observations where date between ? and ?) and date between ? and ?) MAXDEWTIME ".
	", (select MAX(DATE) FROM OBSERVATIONS WHERE HEAT_INDEX = (Select MAX(HEAT_INDEX) from observations where date between ? and ?) and date between ? and ?) MAXHITIME ".
	", (select MAX(DATE) FROM OBSERVATIONS WHERE RAIN_RATE = (Select MAX(RAIN_RATE) from observations where date between ? and ?) and date between ? and ?) MAXRAINTIME ".
	", (select MAX(DATE) FROM OBSERVATIONS WHERE GUST_SPEED = (Select MAX(GUST_SPEED) from observations where date between ? and ?) and date between ? and ?) MAXGUSTTIME ".
	", (select GUST_DIRECTION FROM OBSERVATIONS WHERE GUST_SPEED = (Select MAX(GUST_SPEED) from observations where date between ? and ?) and date between ? and ? LIMIT 1) MAXGUSTDIR ".
	", (select MAX(DATE) FROM OBSERVATIONS WHERE TEMPERATURE = (Select MIN(TEMPERATURE) from observations where date between ? and ?) and date between ? and ?) MINTEMPTIME ".
	", (select MAX(DATE) FROM OBSERVATIONS WHERE HUMIDITY = (Select MIN(HUMIDITY) from observations where date between ? and ?) and date between ? and ?) MINHUMTIME ".
	", (select MAX(DATE) FROM OBSERVATIONS WHERE DEWPOINT = (Select MIN(DEWPOINT) from observations where date between ? and ?) and date between ? and ?) MINDEWTIME ".
	", (select MAX(DATE) FROM OBSERVATIONS WHERE WINDCHILL = (Select MIN(WINDCHILL) from observations where date between ? and ?) and date between ? and ?) MINWCTIME ".
	"from observations where date between ? and ?;";
$statement->bind_param("ssssssssssssssssssssssssssssssssssssssssssssss", $dateStart, $dateEnd, $dateStart, $dateEnd, $dateStart, $dateEnd, $dateStart, $dateEnd, $dateStart, $dateEnd, $dateStart, $dateEnd, $dateStart, $dateEnd, $dateStart, $dateEnd, $dateStart, $dateEnd, $dateStart, $dateEnd, $dateStart, $dateEnd, $dateStart, $dateEnd, $dateStart, $dateEnd, $dateStart, $dateEnd, $dateStart, $dateEnd, $dateStart, $dateEnd, $dateStart, $dateEnd, $dateStart, $dateEnd, $dateStart, $dateEnd, $dateStart, $dateEnd, $dateStart, $dateEnd, $dateStart, $dateEnd, $dateStart, $dateEnd);
			
```

This works when going against a mysql install on a windows box but not against the Linux box.  Any suggestions would be greatly appreciated.

~Peter

---

