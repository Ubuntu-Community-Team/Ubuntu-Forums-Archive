---
title: "is my LAMP server beeing hacked??"
date: 2010-03-12
forum: Server Platforms
---

### Post by envis on 2010-03-12
Hello

i am just concerned about the health of my server. i run a few sites and i dont really have that much traffic on any of them. today i was finding the server slow so i turned on server_status on my apache in an attempt to monitor the traffic. i have turned on server_status a couple of times before but i never remember seeing what i see in there today...

heres what my server_status page looks like:

```

Apache Server Status for mydomain1.org

Server Version: Apache/2.2.3 (Ubuntu) PHP/5.2.1 mod_ssl/2.2.3 OpenSSL/0.9.8c
Server Built: Feb 4 2008 20:21:24

Current Time: Friday, 12-Mar-2010 01:29:55 EST
Restart Time: Friday, 12-Mar-2010 01:00:52 EST
Parent Server Generation: 0
Server uptime: 29 minutes 3 seconds
Total accesses: 4884 - Total Traffic: 38.1 MB
CPU Usage: u1 s1.16 cu0 cs0 - .124% CPU load
2.8 requests/sec - 22.4 kB/second - 8.0 kB/request
25 requests currently being processed, 7 idle workers

K_KKKKKKWWKWKKK_KKKKKKKK_KWW____................................
................................................................
................................................................
................................................................
................................................................
................................................................
................................................................
....................................................

Scoreboard Key:
"_" Waiting for Connection, "S" Starting up, "R" Reading Request,
"W" Sending Reply, "K" Keepalive (read), "D" DNS Lookup,
"C" Closing connection, "L" Logging, "G" Gracefully finishing,
"I" Idle cleanup of worker, "." Open slot with no current process

Srv	PID	Acc	M	CPU 	SS	Req	Conn	Child	Slot	Client	VHost	Request
0-0	5280	3/24/196	K 	0.13	0	10648	17.2	0.25	2.15 	70.80.188.198	mydomain1.org	POST /wmo_post?sureorunsure=sure HTTP/1.1
1-0	5433	0/2/158	_ 	0.00	1	0	0.0	0.01	0.73 	97.101.11.217	mydomain2.com.com	GET /services/discovr/assets/blah1.swf HTTP/1.1
2-0	5232	44/56/170	K 	0.11	4	2	117.3	0.15	0.70 	70.80.188.198	mydomain2.com.com	GET /nab/xmlhometoppages?test=1&genre=1&page=1 HTTP/1.1
3-0	5165	1/53/158	K 	0.37	6	15	0.0	0.61	1.14 	89.159.204.37	mydomain2.com.com	GET /rss?test=0&genre=&alpha=&order=rating+DESC%2C+last
4-0	5209	8/29/146	K 	0.05	0	0	30.0	0.08	1.46 	97.101.11.217	mydomain1.org	GET /common_files/pics/play1.gif HTTP/1.1
5-0	5434	1/1/216	K 	0.00	1	0	5.4	0.01	3.66 	97.101.11.217	mydomain2.com.com	GET /services/discovr/assets/blah1.swf HTTP/1.1
6-0	5310	1/15/159	K 	0.05	11	6	0.0	0.10	0.85 	76.6.90.135	mydomain2.com.com	GET / HTTP/1.1
7-0	5339	6/22/183	K 	0.06	0	0	49.6	0.17	1.51 	97.101.11.217	mydomain1.org	GET /common_files/pics/thumbsdown2.gif HTTP/1.1
8-0	5251	1/2/114	W 	0.00	257	0	0.4	0.00	0.77 	70.80.188.198	mydomain1.org	GET /suckice2?letter=3&auto=go HTTP/1.1
9-0	5252	0/2/99	W 	0.00	254	0	0.0	0.01	0.59 	70.80.188.198	mydomain1.org	GET /mulinkchecker?page=3 HTTP/1.1
10-0	5392	1/4/136	K 	0.00	4	0	0.2	0.00	1.39 	58.107.184.78	mydomain5.net	GET /databob?vid=44246 HTTP/1.1
11-0	5258	0/1/96	W 	0.01	258	0	0.0	0.01	0.59 	70.80.188.198	mydomain1.org	GET /suckice3?letter=4&auto=go HTTP/1.1
12-0	5410	4/4/135	K 	0.01	7	0	25.6	0.02	1.09 	71.51.73.81	mydomain1.org	GET /common_files/pics/play1.gif HTTP/1.1
13-0	5341	5/12/117	K 	0.08	0	0	1.9	0.07	0.87 	97.101.11.217	mydomain1.org	GET /common_files/pics/thumbsup2.gif HTTP/1.1
14-0	5342	1/9/125	K 	0.07	5	425	22.8	0.06	0.87 	89.159.204.37	mydomain1.org	GET /rss?test=0&genre=&alpha=&order=rating+DESC%2C+last
15-0	5175	0/46/105	_ 	0.21	0	0	0.0	0.31	0.79 	97.101.11.217	mydomain1.org	GET /common_files/pics/thumbsup2.gif HTTP/1.1
16-0	5411	6/6/137	K 	0.01	2	0	62.7	0.06	0.53 	71.51.73.81	mydomain1.org	GET /common_files/pics/play2.gif HTTP/1.1
17-0	5412	6/6/156	K 	0.00	7	0	27.3	0.03	1.08 	71.51.73.81	mydomain1.org	GET /common_files/pics/thumbsdown2.gif HTTP/1.1
18-0	5413	4/4/153	K 	0.00	7	0	4.9	0.00	1.29 	71.51.73.81	mydomain1.org	GET /common_files/pics/thumbsup2.gif HTTP/1.1
19-0	5414	4/4/109	K 	0.00	7	0	9.3	0.01	0.68 	71.51.73.81	mydomain1.org	GET /common_files/pics/crazy_eye.gif HTTP/1.1
20-0	5285	5/25/106	K 	0.05	0	0	6.0	0.10	0.51 	97.101.11.217	mydomain1.org	GET /common_files/pics/crazy_eye.gif HTTP/1.1
21-0	5415	5/5/81	K 	0.00	7	0	45.9	0.04	0.36 	71.51.73.81	mydomain1.org	GET /common_files/pics/error.gif HTTP/1.1
22-0	5416	5/5/99	K 	0.00	1	0	8.2	0.01	0.66 	68.117.247.181	mydomain4.com	GET /?link=http%3A%2F%2Fwww.allstar-movies.com%2Ftag%2Favatar%2
23-0	5417	3/3/163	K 	0.00	4	0	5.9	0.01	1.26 	68.117.247.181	mydomain1.org	GET /common_files/test.css HTTP/1.1
24-0	5418	0/1/102	_ 	0.00	0	14	0.0	0.00	0.53 	70.80.188.198	mydomain3.com	GET /supertest?typez=POST HTTP/1.1
25-0	5289	6/18/81	K 	0.03	0	0	22.4	0.07	0.60 	97.101.11.217	mydomain1.org	GET /common_files/pics/error.gif HTTP/1.1
26-0	5435	0/0/80	W 	0.00	1	0	0.0	0.00	0.67 	97.101.11.217	backstage.mydomain1.org	GET /protected_content/63337/userspics/81.jpg HTTP/1.1
27-0	5436	0/0/105	W 	0.20	0	0	0.0	0.00	0.28 	70.80.188.198	mydomain1.org	GET /server-status HTTP/1.1
28-0	5437	0/0/32	_ 	0.06	0	0	0.0	0.00	2.77 	::1	mydomain2.com.com	GET / HTTP/1.0
29-0	5438	0/0/76	_ 	0.00	0	4	0.0	0.00	0.37 	::1	mydomain2.com.com	GET / HTTP/1.0
30-0	5439	0/0/51	_ 	0.04	0	7	0.0	0.00	0.36 	::1	mydomain2.com.com	GET / HTTP/1.0
31-0	5440	0/0/49	_ 	0.00	0	4	0.0	0.00	0.35 	::1	mydomain2.com.com	GET / HTTP/1.0
32-0	-	0/0/51	. 	0.05	450	0	0.0	0.00	0.26 	::1	mydomain2.com.com	GET / HTTP/1.0
33-0	-	0/0/33	. 	0.00	690	4	0.0	0.00	0.27 	::1	mydomain2.com.com	GET / HTTP/1.0
34-0	-	0/0/70	. 	0.00	689	4	0.0	0.00	0.76 	::1	mydomain2.com.com	GET / HTTP/1.0
35-0	-	0/0/46	. 	0.00	684	4	0.0	0.00	0.33 	::1	mydomain2.com.com	GET / HTTP/1.0
36-0	-	0/0/93	. 	0.14	412	7	0.0	0.00	0.59 	::1	mydomain2.com.com	GET / HTTP/1.0
37-0	-	0/0/41	. 	0.00	688	4	0.0	0.00	0.28 	::1	mydomain2.com.com	GET / HTTP/1.0
38-0	-	0/0/27	. 	0.00	687	8	0.0	0.00	0.08 	::1	mydomain2.com.com	GET / HTTP/1.0
39-0	-	0/0/31	. 	0.00	686	8	0.0	0.00	0.38 	::1	mydomain2.com.com	GET / HTTP/1.0
40-0	-	0/0/39	. 	0.08	1124	7	0.0	0.00	0.17 	::1	mydomain2.com.com	GET / HTTP/1.0
41-0	-	0/0/30	. 	0.00	1125	0	0.0	0.00	0.20 	::1	mydomain2.com.com	GET / HTTP/1.0
42-0	-	0/0/9	. 	0.00	1133	0	0.0	0.00	0.12 	::1	mydomain2.com.com	GET / HTTP/1.0
43-0	-	0/0/22	. 	0.00	1173	5	0.0	0.00	0.11 	::1	mydomain2.com.com	GET / HTTP/1.0
44-0	-	0/0/20	. 	0.00	1196	12	0.0	0.00	0.08 	::1	mydomain2.com.com	GET / HTTP/1.0
45-0	-	0/0/7	. 	0.00	1207	8	0.0	0.00	0.03 	::1	mydomain2.com.com	GET / HTTP/1.0
46-0	-	0/0/17	. 	0.01	1193	3	0.0	0.00	0.21 	::1	mydomain2.com.com	GET / HTTP/1.0
47-0	-	0/0/12	. 	0.02	1134	0	0.0	0.00	0.09 	::1	mydomain2.com.com	GET / HTTP/1.0
48-0	-	0/0/13	. 	0.00	1203	3	0.0	0.00	0.03 	::1	mydomain2.com.com	GET / HTTP/1.0
49-0	-	0/0/9	. 	0.00	1193	3	0.0	0.00	0.02 	::1	mydomain2.com.com	GET / HTTP/1.0
50-0	-	0/0/40	. 	0.05	1139	6	0.0	0.00	0.29 	::1	mydomain2.com.com	GET / HTTP/1.0
51-0	-	0/0/28	. 	0.02	1057	0	0.0	0.00	0.22 	::1	mydomain2.com.com	GET / HTTP/1.0
52-0	-	0/0/11	. 	0.00	1217	9	0.0	0.00	0.03 	::1	mydomain2.com.com	GET / HTTP/1.0
53-0	-	0/0/67	. 	0.06	785	7	0.0	0.00	0.61 	::1	mydomain2.com.com	GET / HTTP/1.0
54-0	-	0/0/22	. 	0.00	1177	9	0.0	0.00	0.05 	::1	mydomain2.com.com	GET / HTTP/1.0
55-0	-	0/0/41	. 	0.00	1181	0	0.0	0.00	0.36 	::1	mydomain2.com.com	GET / HTTP/1.0
56-0	-	0/0/10	. 	0.00	1189	8	0.0	0.00	0.01 	::1	mydomain2.com.com	GET / HTTP/1.0
57-0	-	0/0/29	. 	0.02	1172	21	0.0	0.00	0.16 	::1	mydomain2.com.com	GET / HTTP/1.0
58-0	-	0/0/19	. 	0.01	1174	7	0.0	0.00	0.10 	::1	mydomain2.com.com	GET / HTTP/1.0
59-0	-	0/0/32	. 	0.00	1191	7	0.0	0.00	0.30 	::1	mydomain2.com.com	GET / HTTP/1.0
60-0	-	0/0/3	. 	0.00	1624	4	0.0	0.00	0.00 	::1	mydomain2.com.com	GET / HTTP/1.0
61-0	-	0/0/2	. 	0.00	1628	8	0.0	0.00	0.00 	::1	mydomain2.com.com	GET / HTTP/1.0
62-0	-	0/0/32	. 	0.02	1387	0	0.0	0.00	0.09 	::1	mydomain2.com.com	GET / HTTP/1.0
63-0	-	0/0/37	. 	0.09	1422	0	0.0	0.00	0.18 	::1	mydomain2.com.com	GET / HTTP/1.0
64-0	-	0/0/2	. 	0.01	1631	3	0.0	0.00	0.10 	::1	mydomain2.com.com	GET / HTTP/1.0
65-0	-	0/0/46	. 	0.04	1478	7	0.0	0.00	0.18 	::1	mydomain2.com.com	GET / HTTP/1.0

```

what is concerning me is all these seemingly empty requests

like this

59-0	-	0/0/32	. 	0.00	1191	7	0.0	0.00	0.30 	::1	mydomain2.com.com	GET / HTTP/1.0

note that mydomain2.com points to my server but not mydomain2.com.com that must just be a misconfiguration but what i wonder is what is making all these requests to just GET / HTTP/1.0 from the ip ::1




if i look on my other server, i dont have these weird requests, but i have there other weird requests that i do not have on the first server

```

Apache Server Status for domain10.com

Server Version: Apache/2.2.8 (Ubuntu) PHP/5.2.4-2ubuntu5.3 with Suhosin-Patch
Server Built: Jun 25 2008 13:54:43

Current Time: Friday, 12-Mar-2010 01:27:01 EST
Restart Time: Friday, 12-Mar-2010 01:08:48 EST
Parent Server Generation: 0
Server uptime: 18 minutes 12 seconds
Total accesses: 1200 - Total Traffic: 5.1 MB
CPU Usage: u3.65 s.31 cu.05 cs0 - .367% CPU load
1.1 requests/sec - 4897 B/second - 4456 B/request
7 requests currently being processed, 6 idle workers

__K.K._.WK.___KK.K..............................................
................................................................
................................................................
................................................................

Scoreboard Key:
"_" Waiting for Connection, "S" Starting up, "R" Reading Request,
"W" Sending Reply, "K" Keepalive (read), "D" DNS Lookup,
"C" Closing connection, "L" Logging, "G" Gracefully finishing,
"I" Idle cleanup of worker, "." Open slot with no current process

Srv	PID	Acc	M	CPU 	SS	Req	Conn	Child	Slot	Client	VHost	Request
0-0	1198	0/4/70	_ 	0.00	2	0	0.0	0.02	0.20 	70.80.188.198	domain10.com	GET /server-status HTTP/1.1
1-0	1199	0/5/71	_ 	0.07	5	64	0.0	0.02	0.32 	67.212.81.217	127.0.1.1	HEAD /xxx/xmlcams?category=Girl&page=1&match=&startwith= HTTP/1
2-0	1200	3/10/83	K 	0.17	0	1	6.6	0.02	0.24 	218.186.9.243	domain11.com	GET /image_verification?name=51539 HTTP/1.0
3-0	-	0/0/79	. 	0.47	21	0	0.0	0.00	0.40 	::1	127.0.1.1	OPTIONS * HTTP/1.0
4-0	792	1/26/76	K 	0.45	13	0	0.4	0.08	0.35 	67.253.29.9	domain10.com	GET /leaderboard HTTP/1.1
5-0	-	0/0/84	. 	0.32	48	0	0.0	0.00	0.19 	::1	127.0.1.1	OPTIONS * HTTP/1.0
6-0	1090	0/18/76	_ 	0.34	2	319	0.0	0.15	0.49 	67.212.81.217	127.0.1.1	HEAD /xxx/xmlcams?category=Girl&page=1&match=&startwith= HTTP/1
7-0	-	0/0/75	. 	0.04	17	0	0.0	0.00	0.21 	::1	127.0.1.1	OPTIONS * HTTP/1.0
8-0	963	0/12/53	W 	0.18	0	0	0.0	0.03	0.28 	70.80.188.198	domain10.com	GET /server-status HTTP/1.1
9-0	964	1/20/68	K 	0.20	12	1042	9.6	0.04	0.20 	75.155.180.164	domain10.com	GET /xmlshownsresults?site=3064&page=59&order=time_DESC&alpha=a
10-0	-	0/0/83	. 	0.36	25	0	0.0	0.00	0.47 	::1	127.0.1.1	OPTIONS * HTTP/1.0
11-0	1001	0/16/58	_ 	0.32	0	106	0.0	0.10	0.27 	67.212.81.217	127.0.1.1	HEAD /xxx/xmlcams?category=Girl&page=1&match=&startwith= HTTP/1
12-0	1106	0/11/46	_ 	0.20	2	86	0.0	0.06	0.20 	67.212.81.217	127.0.1.1	HEAD /xxx/xmlcams?category=Girl&page=1&match=&startwith= HTTP/1
13-0	1003	0/20/63	_ 	0.29	0	89	0.0	0.19	0.32 	67.212.81.217	127.0.1.1	HEAD /xxx/xmlcams?category=Girl&page=1&match=&startwith= HTTP/1
14-0	1202	1/9/60	K 	0.05	0	5	0.3	0.08	0.24 	218.186.9.243	domain11.com	GET /xmlchat?section=2&subsection=808&userID=0&order=posting_ti
15-0	1203	1/5/23	K 	0.11	7	0	0.1	0.01	0.09 	218.186.9.12	domain11.com	GET /play2.gif HTTP/1.0
16-0	-	0/0/66	. 	0.00	26	0	0.0	0.00	0.19 	::1	127.0.1.1	OPTIONS * HTTP/1.0
17-0	655	1/33/38	K 	0.31	0	11	1.1	0.20	0.23 	218.186.9.243	domain11.com	GET /xmltags?pageID=808&order=posting_time&page=1 HTTP/1.0
18-0	-	0/0/6	. 	0.08	450	0	0.0	0.00	0.01 	::1	127.0.1.1	OPTIONS * HTTP/1.0
19-0	-	0/0/19	. 	0.11	470	0	0.0	0.00	0.20 	::1	127.0.1.1	OPTIONS * HTTP/1.0
20-0	-	0/0/3	. 	0.08	463	0	0.0	0.00	0.00 	::1	127.0.1.1	OPTIONS * HTTP/1.0

```


can anyone tell me if these look right?

---

