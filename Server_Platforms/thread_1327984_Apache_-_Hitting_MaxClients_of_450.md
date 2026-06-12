---
title: "Apache - Hitting MaxClients of 450"
date: 2009-11-16
forum: Server Platforms
---

### Post by victorhooi on 2009-11-16
heya,

This is a slight continuation of an earlier question:

[http://ubuntuforums.org/showthread.php?t=1310139](http://ubuntuforums.org/showthread.php?t=1310139)

Now, our Apache ServerLimit and MaxClients are indeed set to 450. However, this was only ever meant to be a temporary dirty hack.

Our traffic is around 20,000 hits a day, it's a PHP/MySQL CMS that shows a few info pages and shows some query results for products in a database. It doesn't really do that much heavy lifting outside of this.

The hardware is a Amazon EC2 small instance (1.7 Gb of RAM).

This is the prefork settings:

```
<IfModule mpm_prefork_module>
KeepAlive           On
KeepAliveTimeout     7
StartServers          5
MinSpareServers       5
MaxSpareServers      10
MaxClients          450
ServerLimit         450
MaxRequestsPerChild   0
</IfModule>
```

Checking ps aux, I have:

```
xxxxxxxxx@domU-XXXXXXXXX:/etc/apache2$ ps -eo pid,user,rss,vsz,args | grep apache
 2333 root     11092  39084 /usr/sbin/apache2 -k start
 3704 www-data 11060  41292 /usr/sbin/apache2 -k start
 3826 www-data 10016  39844 /usr/sbin/apache2 -k start
 3954 www-data 11976  41612 /usr/sbin/apache2 -k start
 4061 www-data 11844  41668 /usr/sbin/apache2 -k start
 4064 www-data 10988  40676 /usr/sbin/apache2 -k start
 4084 www-data 11804  41428 /usr/sbin/apache2 -k start
 4086 www-data 10192  39828 /usr/sbin/apache2 -k start
 4099 www-data 11876  41748 /usr/sbin/apache2 -k start
 4100 www-data 10980  40668 /usr/sbin/apache2 -k start
 4102 www-data  8952  39724 /usr/sbin/apache2 -k start
 4107 www-data 11856  41860 /usr/sbin/apache2 -k start
 4108 www-data  9952  39604 /usr/sbin/apache2 -k start
 4109 www-data     0      0 [apache2] <defunct>
 4114 www-data  7172  39724 /usr/sbin/apache2 -k start
 4115 www-data 10968  40668 /usr/sbin/apache2 -k start
 4122 www-data 11888  41844 /usr/sbin/apache2 -k start
 4123 www-data 11584  41444 /usr/sbin/apache2 -k start
 4124 www-data  7036  39596 /usr/sbin/apache2 -k start
 4125 www-data  6744  39084 /usr/sbin/apache2 -k start
 4126 www-data  9532  39552 /usr/sbin/apache2 -k start
 4127 www-data 10112  39812 /usr/sbin/apache2 -k start
 4128 www-data  6600  39084 /usr/sbin/apache2 -k start
 4129 www-data  6736  39084 /usr/sbin/apache2 -k start
 4130 www-data  7004  39596 /usr/sbin/apache2 -k start
 4131 www-data  6740  39084 /usr/sbin/apache2 -k start
 4132 www-data 11616  41596 /usr/sbin/apache2 -k start
 4134 www-data  7024  39588 /usr/sbin/apache2 -k start
 4135 www-data 11808  41516 /usr/sbin/apache2 -k start
 4136 www-data  7008  39460 /usr/sbin/apache2 -k start
 4137 www-data  6988  39460 /usr/sbin/apache2 -k start
 4139 1003       796   3040 grep --color=auto apache
victorhooi@domU-12-31-39-02-B6-34:/etc/apache2$
```

Is something weird here, or is this all per normal?

Any particular diagnostics I can run, or troubleshooting advice I should try?

Cheers,
Victor

---

### Post by Lars Noodén on 2009-11-16
> **victorhooi said:**
> 

```
xxxxxxxxx@domU-XXXXXXXXX:/etc/apache2$ ps -eo pid,user,rss,vsz,args | grep apache
```


using ps with the option **--forest** will give a clearer picture of which process has forked what.  

ps --forest -eo pid,user,rss,vsz,args | less

---

### Post by victorhooi on 2009-11-16
heya,

Hmm, I did that, and they all seemed to fork from the same apache process:

```
11570 root       120   2108 udevd --daemon                                                                                    
27337 root      2720   8220 /usr/sbin/munin-node                                                                              
 7962 root     11092  39084 /usr/sbin/apache2 -k start                                                                        
 6854 www-data 10056  39840  \_ /usr/sbin/apache2 -k start                                                                    
 7309 www-data 11828  41448  \_ /usr/sbin/apache2 -k start                                                                    
 7341 www-data 11372  41216  \_ /usr/sbin/apache2 -k start                                                                    
 7712 www-data 12108  41808  \_ /usr/sbin/apache2 -k start                                                                    
 7740 www-data 11664  41472  \_ /usr/sbin/apache2 -k start                                                                    
 7829 www-data 11964  41500  \_ /usr/sbin/apache2 -k start                                                                    
 7837 www-data 11284  40884  \_ /usr/sbin/apache2 -k start                                                                    
 7913 www-data 11320  40884  \_ /usr/sbin/apache2 -k start                                                                    
 7926 www-data 12004  41592  \_ /usr/sbin/apache2 -k start                                                                    
 8042 www-data 11328  40884  \_ /usr/sbin/apache2 -k start                                                                    
 8144 www-data 10988  40600  \_ /usr/sbin/apache2 -k start                                                                    
 8148 www-data  7332  39448  \_ /usr/sbin/apache2 -k start                                                                    
 8155 www-data 11292  41200  \_ /usr/sbin/apache2 -k start                                                                    
 8156 www-data  8768  39648  \_ /usr/sbin/apache2 -k start                                                                    
 8173 www-data  8964  39592  \_ /usr/sbin/apache2 -k start                                                                    
 8175 www-data 12028  41704  \_ /usr/sbin/apache2 -k start                                                                    
 8183 www-data 11972  41840  \_ /usr/sbin/apache2 -k start                                                                    
 8187 www-data 11604  41216  \_ /usr/sbin/apache2 -k start                                                                    
 8214 www-data 11900  41624  \_ /usr/sbin/apache2 -k start                                                                    
 8217 www-data  6984  39084  \_ /usr/sbin/apache2 -k start                                                                    
 8221 www-data 11264  40900  \_ /usr/sbin/apache2 -k start                                                                    
 8228 www-data 11068  40704  \_ /usr/sbin/apache2 -k start                                                                    
 8232 www-data 11972  41940  \_ /usr/sbin/apache2 -k start                                                                    
 8242 www-data 11792  41560  \_ /usr/sbin/apache2 -k start                                                                    
 8251 www-data  9572  39548  \_ /usr/sbin/apache2 -k start                                                                    
 8257 www-data 10004  40592  \_ /usr/sbin/apache2 -k start                                                                    
 8264 www-data 12288  42200  \_ /usr/sbin/apache2 -k start                                                                    
 8266 www-data 10520  40112  \_ /usr/sbin/apache2 -k start                                                                    
 8267 www-data 11064  40668  \_ /usr/sbin/apache2 -k start                                                                    
 8269 www-data 11972  41608  \_ /usr/sbin/apache2 -k start                                                                    
 8277 www-data 10176  39832  \_ /usr/sbin/apache2 -k start                                                                    
 8286 www-data 12104  41860  \_ /usr/sbin/apache2 -k start                                                                    
 8456 www-data 11800  41356  \_ /usr/sbin/apache2 -k start                                                                    
 8557 www-data 11236  40884  \_ /usr/sbin/apache2 -k start                                                                    
 8560 www-data 11796  41408  \_ /usr/sbin/apache2 -k start                                                                    
 8562 www-data 10984  40656  \_ /usr/sbin/apache2 -k start                                                                    
 8563 www-data  7112  39220  \_ /usr/sbin/apache2 -k start                                                                    
 8564 www-data  7400  39600  \_ /usr/sbin/apache2 -k start                                                                    
 8572 www-data 11244  40884  \_ /usr/sbin/apache2 -k start                                                                    
 8579 www-data  7388  39600  \_ /usr/sbin/apache2 -k start                                                                    
 8581 www-data  7112  39220  \_ /usr/sbin/apache2 -k start                                                                    
 8585 www-data 11796  41384  \_ /usr/sbin/apache2 -k start                                                                    
 8604 www-data  9680  39832  \_ /usr/sbin/apache2 -k start                                                                    
 8619 www-data 11940  41600  \_ /usr/sbin/apache2 -k start                                                                    
 8628 www-data  7500  39600  \_ /usr/sbin/apache2 -k start                                                                    
 8635 www-data  7464  39576  \_ /usr/sbin/apache2 -k start                                                                    
 8638 www-data  7328  39456  \_ /usr/sbin/apache2 -k start                                                                    
 8647 www-data 11676  41600  \_ /usr/sbin/apache2 -k start                                                                    
 8654 www-data  7508  39608  \_ /usr/sbin/apache2 -k start                                                                    
 8656 www-data 11724  41328  \_ /usr/sbin/apache2 -k start                                                                    
 8663 www-data  7116  39084  \_ /usr/sbin/apache2 -k start                                                                    
 8669 www-data 12080  41808  \_ /usr/sbin/apache2 -k start                                                                    
 8672 www-data  7356  39456  \_ /usr/sbin/apache2 -k start                                                                    
 8682 www-data 10000  39832  \_ /usr/sbin/apache2 -k start                                                                    
 8686 www-data 11228  40884  \_ /usr/sbin/apache2 -k start                                                                    
 8687 www-data  7340  39456  \_ /usr/sbin/apache2 -k start                                                                    
 8693 www-data  7408  39600  \_ /usr/sbin/apache2 -k start                                                                    
 8706 www-data 11204  40956  \_ /usr/sbin/apache2 -k start                                                                    
 8709 www-data 12040  41636  \_ /usr/sbin/apache2 -k start                                                                    
 8713 www-data 11304  40884  \_ /usr/sbin/apache2 -k start                                                                    
 8716 www-data  7412  39576  \_ /usr/sbin/apache2 -k start                                                                    
 8719 www-data 12128  41912  \_ /usr/sbin/apache2 -k start                                                                    
 8721 www-data 12044  41612  \_ /usr/sbin/apache2 -k start                                                                    
 8723 www-data  9424  39576  \_ /usr/sbin/apache2 -k start                                                                    
 8733 www-data  6984  39084  \_ /usr/sbin/apache2 -k start                                                                    
 8993 www-data 12620  42328  \_ /usr/sbin/apache2 -k start                                                                    
 8999 www-data  7352  39456  \_ /usr/sbin/apache2 -k start                                                                    
 9000 www-data  7408  39600  \_ /usr/sbin/apache2 -k start                                                                    
 9004 www-data  6984  39084  \_ /usr/sbin/apache2 -k start                                                                    
 9009 www-data  7508  39712  \_ /usr/sbin/apache2 -k start                                                                    
 9019 www-data 11860  41404  \_ /usr/sbin/apache2 -k start                                                                    
 9024 www-data 10728  40664  \_ /usr/sbin/apache2 -k start                                                                    
 9034 www-data  7348  39456  \_ /usr/sbin/apache2 -k start                                                                    
 9041 www-data 11720  41408  \_ /usr/sbin/apache2 -k start                                                                    
 9045 www-data  6984  39084  \_ /usr/sbin/apache2 -k start                                                                    
 9058 www-data 11092  40704  \_ /usr/sbin/apache2 -k start                                                                    
 9061 www-data 11608  41224  \_ /usr/sbin/apache2 -k start                                                                    
 9062 www-data 11052  40656  \_ /usr/sbin/apache2 -k start                                                                    
 9063 www-data  6984  39084  \_ /usr/sbin/apache2 -k start                                                                    
 9068 www-data  7340  39456  \_ /usr/sbin/apache2 -k start                                                                    
 9073 www-data 11080  40712  \_ /usr/sbin/apache2 -k start                                                                    
 9096 www-data  7460  39592  \_ /usr/sbin/apache2 -k start                                                                    
 9099 www-data 11544  41312  \_ /usr/sbin/apache2 -k start                                                                    
 9108 www-data 10996  40668  \_ /usr/sbin/apache2 -k start                                                                    
 9109 www-data  8840  39664  \_ /usr/sbin/apache2 -k start                                                                    
 9112 www-data 11236  40884  \_ /usr/sbin/apache2 -k start                                                                    
 9114 www-data  7464  39576  \_ /usr/sbin/apache2 -k start                                                                    
 9120 www-data  7320  39464  \_ /usr/sbin/apache2 -k start                                                                    
 9122 www-data 11640  41592  \_ /usr/sbin/apache2 -k start                                                                    
 9279 www-data 11900  41912  \_ /usr/sbin/apache2 -k start                                                                    
 9292 www-data 11604  41208  \_ /usr/sbin/apache2 -k start                                                                    
 9294 www-data 11268  40892  \_ /usr/sbin/apache2 -k start                                                                    
 9296 www-data  7084  39084  \_ /usr/sbin/apache2 -k start                                                                    
 9327 www-data 11704  41380  \_ /usr/sbin/apache2 -k start                                                                    
 9329 www-data  7408  39600  \_ /usr/sbin/apache2 -k start                                                                    
 9334 www-data 11636  41248  \_ /usr/sbin/apache2 -k start                                                                    
 9396 www-data  7524  39600  \_ /usr/sbin/apache2 -k start                                                                    
 9397 www-data  9616  39572  \_ /usr/sbin/apache2 -k start                                                                    
 9409 www-data  7072  39084  \_ /usr/sbin/apache2 -k start                                                                    
 9417 www-data  7384  39600  \_ /usr/sbin/apache2 -k start                                                                    
 9426 www-data  6984  39084  \_ /usr/sbin/apache2 -k start                                                                    
 9439 www-data 11240  40884  \_ /usr/sbin/apache2 -k start                                                                    
14460 www-data 12052  41628  \_ /usr/sbin/apache2 -k start                                                                    
15294 www-data 11324  40892  \_ /usr/sbin/apache2 -k start                                                                    
15725 www-data 11088  40660  \_ /usr/sbin/apache2 -k start                                                                    
15783 www-data 11792  41404  \_ /usr/sbin/apache2 -k start                                                                    
15798 www-data 11772  41404  \_ /usr/sbin/apache2 -k start                                                                    
15809 www-data 11576  41140  \_ /usr/sbin/apache2 -k start                                                                    
15812 www-data  9968  39576  \_ /usr/sbin/apache2 -k start                                                                    
15813 www-data 12008  41824  \_ /usr/sbin/apache2 -k start                                                                    
15815 www-data 11308  40884  \_ /usr/sbin/apache2 -k start                                                                    
15832 www-data  7704  39600  \_ /usr/sbin/apache2 -k start                                                                    
15833 www-data 11624  41016  \_ /usr/sbin/apache2 -k start                                                                    
15834 www-data 11048  40720  \_ /usr/sbin/apache2 -k start                                                                    
15841 www-data 11028  40656  \_ /usr/sbin/apache2 -k start                                                                    
16045 www-data  9620  39580  \_ /usr/sbin/apache2 -k start                                                                    
16098 www-data 11660  41352  \_ /usr/sbin/apache2 -k start                                                                    
16105 www-data 11632  41592  \_ /usr/sbin/apache2 -k start                                                                    
16115 www-data 11344  40892  \_ /usr/sbin/apache2 -k start                                                                    
16119 www-data 11312  41140  \_ /usr/sbin/apache2 -k start                                                                    
16120 www-data 11856  41456  \_ /usr/sbin/apache2 -k start                                                                    
16121 www-data 11004  40664  \_ /usr/sbin/apache2 -k start                                                                    
16127 www-data 11652  41232  \_ /usr/sbin/apache2 -k start                                                                    
16134 www-data 12284  41848  \_ /usr/sbin/apache2 -k start                                                                    
16135 www-data 11768  41456  \_ /usr/sbin/apache2 -k start                                                                    
16138 www-data 11044  40660  \_ /usr/sbin/apache2 -k start                                                                    
16139 www-data  9428  39584  \_ /usr/sbin/apache2 -k start                                                                    
16140 www-data 11040  40720  \_ /usr/sbin/apache2 -k start                                                                    
16143 www-data  6988  39084  \_ /usr/sbin/apache2 -k start                                                                    
16144 www-data 12128  41760  \_ /usr/sbin/apache2 -k start                                                                    
16149 www-data 10992  40656  \_ /usr/sbin/apache2 -k start                                                                    
16156 www-data 11348  40884  \_ /usr/sbin/apache2 -k start                                                                    
16159 www-data 11252  40884  \_ /usr/sbin/apache2 -k start                                                                    
16162 www-data  9952  39576  \_ /usr/sbin/apache2 -k start                                                                    
16165 www-data 10972  40648  \_ /usr/sbin/apache2 -k start                                                                    
16166 www-data  9436  39584  \_ /usr/sbin/apache2 -k start                                                                    
16173 www-data 11940  41592  \_ /usr/sbin/apache2 -k start                                                                    
16174 www-data 12312  42252  \_ /usr/sbin/apache2 -k start                                                                    
16175 www-data 11864  41688  \_ /usr/sbin/apache2 -k start                                                                    
16182 www-data 11296  41200  \_ /usr/sbin/apache2 -k start                                                                    
16184 www-data  6984  39084  \_ /usr/sbin/apache2 -k start                                                                    
16186 www-data 11888  41596  \_ /usr/sbin/apache2 -k start                                                                    
16190 www-data 11200  40884  \_ /usr/sbin/apache2 -k start                                                                    
16191 www-data  6984  39084  \_ /usr/sbin/apache2 -k start                                                                    
16192 www-data  7304  39428  \_ /usr/sbin/apache2 -k start                                                                    
16200 www-data  7552  39600  \_ /usr/sbin/apache2 -k start                                                                    
16202 www-data  7420  39600  \_ /usr/sbin/apache2 -k start                                                                    
16219 www-data  7504  39600  \_ /usr/sbin/apache2 -k start                                                                    
16223 www-data  7420  39576  \_ /usr/sbin/apache2 -k start                                                                    
16226 www-data  6988  39084  \_ /usr/sbin/apache2 -k start                                                                    
16227 www-data  6988  39084  \_ /usr/sbin/apache2 -k start                                                                    
16228 www-data  6988  39084  \_ /usr/sbin/apache2 -k start                                                                    
16229 www-data  6988  39084  \_ /usr/sbin/apache2 -k start                                                                    
16236 www-data  9436  39568  \_ /usr/sbin/apache2 -k start                                                                    
16241 www-data 11284  40884  \_ /usr/sbin/apache2 -k start                                                                    
16252 www-data 11760  41388  \_ /usr/sbin/apache2 -k start                                                                    
16266 www-data 11784  41448  \_ /usr/sbin/apache2 -k start                                                                    
16276 www-data 11256  40884  \_ /usr/sbin/apache2 -k start                                                                    
16343 www-data 12228  42140  \_ /usr/sbin/apache2 -k start                                                                    
16543 www-data 11040  40664  \_ /usr/sbin/apache2 -k start                                                                    
16550 www-data  7352  39456  \_ /usr/sbin/apache2 -k start                                                                    
16567 www-data  9436  39568  \_ /usr/sbin/apache2 -k start                                                                    
16582 www-data  6988  39084  \_ /usr/sbin/apache2 -k start                                                                    
16583 www-data  7076  39084  \_ /usr/sbin/apache2 -k start                                                                    
16585 www-data  6988  39084  \_ /usr/sbin/apache2 -k start                                                                    
16587 www-data  6988  39084  \_ /usr/sbin/apache2 -k start                                                                    
16590 www-data  6988  39084  \_ /usr/sbin/apache2 -k start                                                                    
16591 www-data  6988  39084  \_ /usr/sbin/apache2 -k start                                                                    
16592 www-data  6988  39084  \_ /usr/sbin/apache2 -k start                                                                    
16593 www-data  6988  39084  \_ /usr/sbin/apache2 -k start                                                                    
16595 www-data 11296  40884  \_ /usr/sbin/apache2 -k start                                                                    
16596 www-data  6988  39084  \_ /usr/sbin/apache2 -k start                                                                    
16600 www-data  8912  39648  \_ /usr/sbin/apache2 -k start                                                                    
16602 www-data  6988  39084  \_ /usr/sbin/apache2 -k start                                                                    
16606 www-data 12128  41728  \_ /usr/sbin/apache2 -k start                                                                    
16611 www-data  9424  39576  \_ /usr/sbin/apache2 -k start                                                                    
16620 www-data 11108  40720  \_ /usr/sbin/apache2 -k start                                                                    
16621 www-data 10464  40628  \_ /usr/sbin/apache2 -k start                                                                    
16622 www-data 10372  40856  \_ /usr/sbin/apache2 -k start                                                                    
16623 www-data 10052  39832  \_ /usr/sbin/apache2 -k start                                                                    
16624 www-data  7408  39600  \_ /usr/sbin/apache2 -k start                                                                    
16637 www-data  9856  39584  \_ /usr/sbin/apache2 -k start                                                                    
16641 www-data 12520  42328  \_ /usr/sbin/apache2 -k start                                                                    
16647 www-data 11252  40900  \_ /usr/sbin/apache2 -k start                                                                    
16654 www-data  9988  40624  \_ /usr/sbin/apache2 -k start                                                                    
16658 www-data  7516  39712  \_ /usr/sbin/apache2 -k start                                                                    
16659 www-data  7504  39608  \_ /usr/sbin/apache2 -k start
16667 www-data  6988  39084  \_ /usr/sbin/apache2 -k start
16668 www-data  9252  39564  \_ /usr/sbin/apache2 -k start
16750 www-data  7356  39456  \_ /usr/sbin/apache2 -k start
16751 www-data 11276  41268  \_ /usr/sbin/apache2 -k start
16752 www-data 12112  42184  \_ /usr/sbin/apache2 -k start
16754 www-data 12064  41932  \_ /usr/sbin/apache2 -k start
16756 www-data 11984  41608  \_ /usr/sbin/apache2 -k start
16759 www-data 12032  41616  \_ /usr/sbin/apache2 -k start
16762 www-data  9560  39532  \_ /usr/sbin/apache2 -k start
16763 www-data  6796  39084  \_ /usr/sbin/apache2 -k start
16764 www-data 12576  42276  \_ /usr/sbin/apache2 -k start
16765 www-data  6760  39084  \_ /usr/sbin/apache2 -k start
16768 www-data 11040  40720  \_ /usr/sbin/apache2 -k start
16769 www-data  6984  39084  \_ /usr/sbin/apache2 -k start
16770 www-data 11944  41648  \_ /usr/sbin/apache2 -k start
16772 www-data  6772  39084  \_ /usr/sbin/apache2 -k start
16773 www-data  6784  39084  \_ /usr/sbin/apache2 -k start
16774 www-data 11072  40696  \_ /usr/sbin/apache2 -k start
16775 www-data  6784  39084  \_ /usr/sbin/apache2 -k start
16777 www-data  7092  39576  \_ /usr/sbin/apache2 -k start
16778 www-data  7168  39576  \_ /usr/sbin/apache2 -k start
16779 www-data 11260  40892  \_ /usr/sbin/apache2 -k start
16780 www-data  7064  39584  \_ /usr/sbin/apache2 -k start
16784 www-data  8820  39648  \_ /usr/sbin/apache2 -k start
16785 www-data  8852  39648  \_ /usr/sbin/apache2 -k start
16787 www-data  8832  39648  \_ /usr/sbin/apache2 -k start
16790 www-data 11248  40884  \_ /usr/sbin/apache2 -k start
16791 www-data 11008  40656  \_ /usr/sbin/apache2 -k start
16793 www-data  9908  40608  \_ /usr/sbin/apache2 -k start
16794 www-data  7032  39456  \_ /usr/sbin/apache2 -k start
16796 www-data  6064  39084  \_ /usr/sbin/apache2 -k start
```

Cheers,
Victor

---

### Post by wojox on 2009-11-16
Its normal to have multiple /usr/sbin/apache2 -k start processes running. I currently have about 50 (on a heavily loaded server).

---

### Post by Lars Noodén on 2009-11-17
> **wojox said:**
> Its normal to have multiple /usr/sbin/apache2 -k start processes running. I currently have about 50 (**on a heavily loaded server**).

Yes, on a heavily loaded server it should start more processes to deal with the increased number of connections.  

Some hardware architectures, like a [sparc](http://www.opensparc.net/about.html) or [mips](http://www.scdsource.com/article.php?id=156) are more suited to that kind of server environment and software than others that might be more visibly "marketed".

---

