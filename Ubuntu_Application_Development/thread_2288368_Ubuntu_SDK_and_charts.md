---
title: "Ubuntu SDK and charts"
date: 2015-07-26
forum: Ubuntu Application Development
---

### Post by Mick21367 on 2015-07-26
Hi,
I'm trying to learn basic qt/qml using Ubuntu SDK to develop apps for Ubuntu Touch. I've created a basic app which stores user data in file (dbdata.js). I want to use this stored data to create a graph (simple bar or line graph), but for the life of me, I can't see how this is done. Is this even possible using qml alone, or do I need to rethink the project?
Thanks
Mick

---

### Post by Mick21367 on 2015-11-08
Been a while since I posted this - quick update. I've been able to use Qchart.js to create a graph in my app. I'm still struggling to pass info from the db to an array which Qchart.js can read and display. I'm trying to get my head around how this would work in javascript. This is my current code

// Chart Data
function getData() {
    var db = LocalStorage.openDatabaseSync("data.sql", "1.0", "mileageDataBase", 10000000);
    var res = [];
    db.transaction(
    function(tx) {
    var rs = tx.executeSql('SELECT * FROM mpg');
    res = rs.rows.item().miles;
    }
 );
 return res;
 }

Any help on how to turn this into something that Qchart can read would be welcome.
Thanks

---

### Post by Mick21367 on 2015-12-27
I finally got this to work. Here is the working code, if anyone is interested. 

// Chart Data
function getData() {
    var db = LocalStorage.openDatabaseSync("data.sql", "1.0", "mileageDataBase", 10000000);
    var ret;
    var res = [];
    var index;
    db.transaction(
    function(tx) {
    var rs = tx.executeSql('SELECT * FROM mpg');
        for (var i=0; i<rs.rows.length; i++) {
            var row = rs.rows.item(i);
            ret = row.miles/row.gallons;
            res.push(ret);
        }
   }
 );
 return res;
 }


You can see it in action on the mileage app on the Ubuntu Touch platform

---

