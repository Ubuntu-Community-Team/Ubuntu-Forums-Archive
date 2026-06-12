---
title: "Modifying haproxy response location URL"
date: 2016-02-29
forum: Server Platforms
---

### Post by chris_vr on 2016-02-29
In a web app I am getting following Location URL
[https://uaa.devtest3.io/login;jsessionid=4A0ADA8DDB7CD09C2B50F4A41945BBDB](https://uaa.devtest3.io/login;jsessionid=4A0ADA8DDB7CD09C2B50F4A41945BBDB) 

Since this internal to the server and to make it work in internet i need to change it to

[https://myexample.com/uaa/login;jsessionid=4A0ADA8DDB7CD09C2B50F4A41945BBDB](https://myexample.com/uaa/login;jsessionid=4A0ADA8DDB7CD09C2B50F4A41945BBDB)

I tried this
acl hdr_location res.hdr(Location) -m found
    rspirep ^Location:\ (https?://uaa.devtest3.io(:[0-9a-zA-Z]+)?)?(/.*) Location:\ myexample.com\3 if hdr_location
its not working .Please help me on this

---

