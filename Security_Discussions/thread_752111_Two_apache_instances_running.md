---
title: "Two apache instances running"
date: 2008-04-11
forum: Security Discussions
---

### Post by morak on 2008-04-11
Hi,

On my Webserver i somehow have a really strange output on running  apache2, just wanted to ask if this has something to do with my Virtual hosts one for port80 and one for port 443? Or what can I do against it? :D

```
ps auwfx | grep apache
```

Here the outpup:
```

root     26477  0.0  0.0   4212   776 pts/0    S+   14:02   0:00          \_ grep apache
root      6033  0.0  0.4 170060  8452 ?        Ss   Apr08   0:00 /usr/sbin/apache2 -k start
www-data  6038  0.0  0.2 170060  4884 ?        S    Apr08   0:00  \_ /usr/sbin/apache2 -k start
root      6074  0.0  0.4 170056  8464 ?        Ss   Apr08   0:00 /usr/sbin/apache2 -k start
www-data  6076  0.0  0.3 170216  6332 ?        S    Apr08   0:00  \_ /usr/sbin/apache2 -k start
www-data  6080  0.0  0.2 170188  6028 ?        S    Apr08   0:00  \_ /usr/sbin/apache2 -k start
www-data  6081  0.0  0.3 170216  6272 ?        S    Apr08   0:00  \_ /usr/sbin/apache2 -k start
root      6110  0.0  0.4 170060  8472 ?        Ss   Apr08   0:00 /usr/sbin/apache2 -k start
www-data  6112  0.0  0.3 170356  6612 ?        S    Apr08   0:00  \_ /usr/sbin/apache2 -k start
www-data  6116  0.0  0.2 170060  4892 ?        S    Apr08   0:00  \_ /usr/sbin/apache2 -k start
www-data  6117  0.0  0.2 170060  4884 ?        S    Apr08   0:00  \_ /usr/sbin/apache2 -k start
root      6134  0.0  0.4 170056  8464 ?        Ss   Apr08   0:00 /usr/sbin/apache2 -k start
www-data  6136  0.0  0.3 170216  6312 ?        S    Apr08   0:00  \_ /usr/sbin/apache2 -k start
www-data  6139  0.0  0.2 170056  4880 ?        S    Apr08   0:00  \_ /usr/sbin/apache2 -k start
www-data  6140  0.0  0.2 170056  4872 ?        S    Apr08   0:00  \_ /usr/sbin/apache2 -k start
www-data  6141  0.0  0.2 170056  4872 ?        S    Apr08   0:00  \_ /usr/sbin/apache2 -k start
root      6159  0.0  0.4 170056  8464 ?        Ss   Apr08   0:00 /usr/sbin/apache2 -k start
www-data  6161  0.0  0.3 170216  6332 ?        S    Apr08   0:00  \_ /usr/sbin/apache2 -k start
www-data  6165  0.0  0.2 170056  4880 ?        S    Apr08   0:00  \_ /usr/sbin/apache2 -k start
www-data  6166  0.0  0.2 170056  4872 ?        S    Apr08   0:00  \_ /usr/sbin/apache2 -k start
root      6182  0.0  0.4 170060 10044 ?        Ss   Apr08   0:01 /usr/sbin/apache2 -k start
www-data  6787  0.0  0.3 170484  7864 ?        S    Apr09   0:00  \_ /usr/sbin/apache2 -k start
www-data  6788  0.0  0.2 170060  5696 ?        S    Apr09   0:00  \_ /usr/sbin/apache2 -k start
www-data  6791  0.0  0.2 170060  5180 ?        S    Apr09   0:00  \_ /usr/sbin/apache2 -k start
www-data  6792  0.0  0.2 170060  5172 ?        S    Apr09   0:00  \_ /usr/sbin/apache2 -k start
www-data  6793  0.0  0.2 170060  5172 ?        S    Apr09   0:00  \_ /usr/sbin/apache2 -k start
root      6853  0.0  0.5 179068 10700 ?        Ss   Apr09   0:00 /usr/sbin/apache2 -k start
www-data  6855  0.0  0.4 179440  8856 ?        S    Apr09   0:00  \_ /usr/sbin/apache2 -k start
www-data  6859  0.0  0.3 179068  6512 ?        S    Apr09   0:00  \_ /usr/sbin/apache2 -k start
www-data  6865  0.0  0.3 179068  6504 ?        S    Apr09   0:00  \_ /usr/sbin/apache2 -k start
root      6880  0.0  0.5 179068 10696 ?        Ss   Apr09   0:00 /usr/sbin/apache2 -k start
www-data  6882  0.0  0.7 224412 15300 ?        S    Apr09   0:00  \_ /usr/sbin/apache2 -k start
www-data  6884  0.0  0.7 224548 15404 ?        S    Apr09   0:00  \_ /usr/sbin/apache2 -k start
www-data  6887  0.0  0.3 179376  8104 ?        S    Apr09   0:00  \_ /usr/sbin/apache2 -k start
root      6914  0.0  0.5 179068 10700 ?        Ss   Apr09   0:00 /usr/sbin/apache2 -k start
www-data  6916  0.0  0.6 222152 12852 ?        S    Apr09   0:00  \_ /usr/sbin/apache2 -k start
www-data  6917  0.0  0.6 222152 12740 ?        S    Apr09   0:00  \_ /usr/sbin/apache2 -k start
www-data  6918  0.0  0.6 222144 12736 ?        S    Apr09   0:00  \_ /usr/sbin/apache2 -k start
www-data  6919  0.0  0.6 222144 12736 ?        S    Apr09   0:00  \_ /usr/sbin/apache2 -k start
www-data  6921  0.0  0.3 179068  6504 ?        S    Apr09   0:00  \_ /usr/sbin/apache2 -k start
root      6968  0.0  0.5 179068 10700 ?        Ss   Apr09   0:00 /usr/sbin/apache2 -k start
www-data  6970  0.0  0.7 228104 14788 ?        S    Apr09   0:00  \_ /usr/sbin/apache2 -k start
www-data  6971  0.0  0.4 179376  8248 ?        S    Apr09   0:00  \_ /usr/sbin/apache2 -k start
www-data  6974  0.0  0.3 179068  6516 ?        S    Apr09   0:00  \_ /usr/sbin/apache2 -k start
www-data  6977  0.0  0.3 179068  6508 ?        S    Apr09   0:00  \_ /usr/sbin/apache2 -k start
root     12833  0.0  0.6 180128 13556 ?        Ss   Apr09   0:00 /usr/sbin/apache2 -k start
www-data 25830  0.0  0.3 180128  7868 ?        S    Apr09   0:00  \_ /usr/sbin/apache2 -k start
www-data 25831  0.0  0.3 180128  7860 ?        S    Apr09   0:00  \_ /usr/sbin/apache2 -k start
root     25846  0.0  0.5 179072 10704 ?        Ss   Apr09   0:00 /usr/sbin/apache2 -k start
www-data 25851  0.0  1.1 287420 22908 ?        S    Apr09   0:01  \_ /usr/sbin/apache2 -k start
www-data 25852  0.0  1.1 286156 22884 ?        S    Apr09   0:00  \_ /usr/sbin/apache2 -k start
www-data 25855  0.0  1.0 285896 20980 ?        S    Apr09   0:00  \_ /usr/sbin/apache2 -k start
www-data 25870  0.0  1.2 288696 26108 ?        S    Apr09   0:01  \_ /usr/sbin/apache2 -k start
www-data 25872  0.0  1.1 287268 23120 ?        S    Apr09   0:01  \_ /usr/sbin/apache2 -k start
www-data 25881  0.0  1.0 286816 21684 ?        S    Apr09   0:01  \_ /usr/sbin/apache2 -k start
www-data 25884  0.0  1.1 287656 23276 ?        S    Apr09   0:00  \_ /usr/sbin/apache2 -k start
root     25925  0.0  0.5 179076 10724 ?        Ss   Apr09   0:00 /usr/sbin/apache2 -k start
www-data 25927  0.0  1.0 285840 20912 ?        S    Apr09   0:00  \_ /usr/sbin/apache2 -k start
www-data 25928  0.0  0.9 285140 20188 ?        S    Apr09   0:00  \_ /usr/sbin/apache2 -k start
www-data 25931  0.0  0.3 179076  6532 ?        S    Apr09   0:00  \_ /usr/sbin/apache2 -k start
www-data 25932  0.0  0.3 179076  6524 ?        S    Apr09   0:00  \_ /usr/sbin/apache2 -k start
root     25958  0.0  0.5 179076 10712 ?        Ss   Apr09   0:00 /usr/sbin/apache2 -k start
www-data 25960  0.0  1.0 285556 20548 ?        S    Apr09   0:00  \_ /usr/sbin/apache2 -k start
www-data 25961  0.0  0.9 282716 19660 ?        S    Apr09   0:00  \_ /usr/sbin/apache2 -k start
www-data 25962  0.0  0.9 282716 19636 ?        S    Apr09   0:00  \_ /usr/sbin/apache2 -k start
www-data 25963  0.0  0.9 282716 19632 ?        S    Apr09   0:00  \_ /usr/sbin/apache2 -k start
www-data 25964  0.0  0.9 282716 19636 ?        S    Apr09   0:00  \_ /usr/sbin/apache2 -k start
www-data 25978  0.0  0.3 179076  6516 ?        S    Apr09   0:00  \_ /usr/sbin/apache2 -k start
www-data 25979  0.0  0.3 179076  6516 ?        S    Apr09   0:00  \_ /usr/sbin/apache2 -k start
www-data 25981  0.0  0.3 179076  6524 ?        S    Apr09   0:00  \_ /usr/sbin/apache2 -k start
root     26001  0.0  0.5 179076 10728 ?        Ss   Apr09   0:00 /usr/sbin/apache2 -k start
www-data 26003  0.0  0.9 285140 20304 ?        S    Apr09   0:00  \_ /usr/sbin/apache2 -k start
www-data 26004  0.0  0.9 285140 20188 ?        S    Apr09   0:00  \_ /usr/sbin/apache2 -k start
www-data 26008  0.0  0.3 179076  6536 ?        S    Apr09   0:00  \_ /usr/sbin/apache2 -k start
root     26028  0.0  0.5 179076 10732 ?        Ss   Apr09   0:00 /usr/sbin/apache2 -k start
www-data 26031  0.0  1.0 285884 20984 ?        S    Apr09   0:00  \_ /usr/sbin/apache2 -k start
www-data 26032  0.0  1.0 285756 20864 ?        S    Apr09   0:00  \_ /usr/sbin/apache2 -k start
www-data 26033  0.0  1.0 285752 20864 ?        S    Apr09   0:00  \_ /usr/sbin/apache2 -k start
www-data 26034  0.0  1.0 285756 20976 ?        S    Apr09   0:00  \_ /usr/sbin/apache2 -k start
www-data 26045  0.0  1.0 285852 20976 ?        S    Apr09   0:00  \_ /usr/sbin/apache2 -k start
www-data 26046  0.0  0.9 285140 20184 ?        S    Apr09   0:00  \_ /usr/sbin/apache2 -k start
www-data 26048  0.0  1.0 286236 21236 ?        S    Apr09   0:01  \_ /usr/sbin/apache2 -k start
www-data 26051  0.0  0.3 179076  6536 ?        S    Apr09   0:00  \_ /usr/sbin/apache2 -k start
root     26379  0.0  0.5 179084 10684 ?        Ss   12:06   0:00 /usr/sbin/apache2 -k start
www-data 26383  0.0  0.3 179084  6504 ?        S    12:06   0:00  \_ /usr/sbin/apache2 -k start
www-data 26384  0.0  0.3 179084  6496 ?        S    12:06   0:00  \_ /usr/sbin/apache2 -k start
www-data 26385  0.0  0.3 179084  6496 ?        S    12:06   0:00  \_ /usr/sbin/apache2 -k start
root     26403  0.0  0.5 179052 10676 ?        Ss   12:07   0:00 /usr/sbin/apache2 -k start
www-data 26405  0.0  0.3 179052  7032 ?        S    12:07   0:00  \_ /usr/sbin/apache2 -k start
www-data 26406  0.0  0.3 179052  7036 ?        S    12:07   0:00  \_ /usr/sbin/apache2 -k start
www-data 26407  0.0  0.4 179432  8536 ?        S    12:07   0:00  \_ /usr/sbin/apache2 -k start
www-data 26408  0.0  0.4 179948  9072 ?        S    12:07   0:00  \_ /usr/sbin/apache2 -k start
www-data 26409  0.0  0.4 179116  8300 ?        S    12:07   0:00  \_ /usr/sbin/apache2 -k start
www-data 26410  0.0  0.4 179124  8380 ?        S    12:07   0:00  \_ /usr/sbin/apache2 -k start
www-data 26422  0.0  0.3 179052  6492 ?        S    12:09   0:00  \_ /usr/sbin/apache2 -k start


```

---

