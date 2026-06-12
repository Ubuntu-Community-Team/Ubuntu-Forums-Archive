---
title: "Time Quota based access control to specific websites"
date: 2009-12-15
forum: Server Platforms
---

### Post by capo on 2009-12-15
UPDATED: you can read my original post below

As I couldn't find any program that did what I wanted I set out to write my own.

My chosen language was C++ because this URL  re-writer need to be FAST (faster than python or perl anyway) and because C++ is a language I am familiar with.

First things first I chose my method of squid integration. Initially I was using the ACL (access control lists) and ensuring that every request pass an external ACL check to be allowed but I found this to be problematic, I’m not sure exactly why but I think it has something to do with the way squid optimises ACL performance. Using url_rewriter_program  alleviated this issue.
As per the requirements from my original post I came up with bellow design (in flow chart form)

[img] http://www.edspcs.com.au/faceblock.png[/img]

The database to fulfill this design has three tables that I set up like this:
```

blacklist:
url(pk) //web address of banned website

request:
id (pk)
srcIP //src ip of web request
requestUrl //url of request rescource
requestTime //time of most recent request

status
flushDate (pk)


CREATE TABLE blacklist
(
url varchar(250) not null primary key
);

CREATE TABLE request
(
id MEDIUMINT  NOT NULL AUTO_INCREMENT,
srcIP varchar(15) not null,
requestUrl varchar(250) not null,
requestTime time not null,
PRIMARY KEY (id)
);


CREATE TABLE status
(
flushDate DATE not null primary key
);

```
And then the implementation was as follows
```

using namespace std;
#include <iostream>
#include <fstream>
#include <mysql++.h>
#include <time.h>
#include <sstream>

#define USER "root"
#define SERVER "localhost"
#define PASS "tstfu646"
#define DB "eo"

//returns the time corosponding to the START of the current access period as a value
struct tm GetAccessPeriod()
{
	time_t rawtime;
	struct tm * timeinfo;
	time ( &rawtime );
	timeinfo = localtime ( &rawtime );	
	mktime ( timeinfo );
	
	if(timeinfo->tm_hour < 12)
	{
		//time is before 12pm
		timeinfo->tm_sec = 0;
		timeinfo->tm_min = 0;
		timeinfo->tm_hour = 0;
		return *timeinfo; //value of timeinfo
	}
	else if(timeinfo->tm_hour >= 12 && timeinfo->tm_hour <= 14)
	{
		//time is between 12pm and 2pm
		timeinfo->tm_sec = 0;
		timeinfo->tm_min = 0;
		timeinfo->tm_hour = 12;
		return *timeinfo; //value of timeinfo
	}
	else if(timeinfo->tm_hour > 14)
	{
		//time is after 2pm
		timeinfo->tm_sec = 0;
		timeinfo->tm_min = 0;
		timeinfo->tm_hour = 14;
		return *timeinfo; //value of timeinfo
	}
}

int GetQuotaSeconds(struct tm * ap)
{
	if(ap->tm_hour < 12)
	{
		return 600;
	}
	else if(ap->tm_hour >= 12 && ap->tm_hour <= 14)
	{
		return 1800;
	}
	else if(ap->tm_hour > 14)
	{
		return 600;
	}
}

//converts a struct tm to a time string that can be used as an sql TIME type
//returns as value
string Stringify(struct tm * time)
{
	string rData = "";
	stringstream out;
	out << time->tm_hour << ":" << time->tm_min << ":" << time->tm_sec;
	rData = out.str();
	return rData;
}

void Tokenise(const string& str, vector<string>& tokens, const string& delimiters = " ")
{
    // Skip delimiters at beginning.
    string::size_type lastPos = str.find_first_not_of(delimiters, 0);
    // Find first "non-delimiter".
    string::size_type pos     = str.find_first_of(delimiters, lastPos);

    while (string::npos != pos || string::npos != lastPos)
    {
        // Found a token, add it to the vector.
        tokens.push_back(str.substr(lastPos, pos - lastPos));
        // Skip delimiters.  Note the "not_of"
        lastPos = str.find_first_not_of(delimiters, pos);
        // Find next "non-delimiter"
        pos = str.find_first_of(delimiters, lastPos);
    }
}

int main()
{

	//local variables:
	string url, ip;
	time_t rawtime; //time/date in seconds since 1970
	mysqlpp::Date lastDate; //use to store the flush date queried from db
	mysqlpp::Date date;	//used to store current date in form to be inserted
	struct tm ap; //start of access period
	struct tm * curTime; //the current time
	mysqlpp::StoreQueryResult res; //stores query results
	mysqlpp::Time::Time t;
	mysqlpp::Time firstRequest; //time of first request
	int ct, fr; //seconds since 00:00 for first request and current time
	char buff [2048];
	vector<string> tokens;
	
	time ( &rawtime );

	ofstream logfile;
	logfile.open("/usr/local/bin/log.txt");
	
	// Connect to db
	mysqlpp::Connection conn;
	if (conn.connect(DB, SERVER, USER, PASS)) 
	{
		mysqlpp::Query query = conn.query("");
		
		//this loop should not exit and should be blocked by cin waiting on input from squid
		while(true)
		{
			// logfile << "started loop at time: " << rawtime <<endl;
		
			cin.getline(buff, 2048);
			Tokenise(string(buff), tokens);
			if(tokens.size() > 1)
			{
				url = tokens[0];
				ip = tokens[1];
			}
			tokens.clear();
			
			//get current date:
			time ( &rawtime );
			date = mysqlpp::Date(rawtime);
			curTime = localtime ( &rawtime );

			// logfile << "request for: " << url << " from: " << ip  << " at: " << Stringify(curTime) <<endl;

			//get last date from DB
			query << "SELECT flushDate FROM status";
					
			if (res = query.store()) 
			{
				lastDate = mysqlpp::Date(res[0][0]);
			}
			query.reset();
			
			if(date.compare(lastDate) > 0) //if it's a new day
			{
				// logfile << "cur date after last date" <<endl;
				
				//flush request
				try
				{
				query << "DELETE FROM request";
				query.execute();
				}
				catch(mysqlpp::BadQuery e)
				{
					// logfile << e.what() <<endl;
				}
				query.reset();
				
				//update date to today
				query << "UPDATE status SET flushDate = '" + date.str() +"'";
				query.execute();
				query.reset();			
			}
			else
			{
				// logfile << "same day" <<endl;
				query << "select url from blacklist where '" + url + "' LIKE url";
				res = query.store();	
				query.reset();
				if(res.num_rows() > 0)
				{
					//quota code goes here:
					// logfile <<  res.num_rows() << " items in blacklist matching " << url <<endl;
					t = mysqlpp::Time::Time(rawtime);
					query << "insert into request (srcIP, requestUrl, requestTime) values('" + ip + "', '" + url + "', '" + t.str() + "')";
					query.execute();
					query.reset();
					ap = GetAccessPeriod();
					curTime = localtime ( &rawtime );

					
					query << "select min(requestTime) as time from request where requestTime > '" + Stringify(&ap) + "' AND srcIP = '" + ip + "'";
					res = query.store();	
					// logfile << res.num_rows() << " requests from: " <<ip <<endl;
					firstRequest = mysqlpp::Time(res[0][0]);
					// logfile << "first request was on: " << firstRequest.str() <<endl;
					fr = firstRequest.second() + 60*firstRequest.minute() + 3600*firstRequest.hour();
					ct = curTime->tm_sec + 60*curTime->tm_min + 3600*curTime->tm_hour;
					fr += GetQuotaSeconds(&ap);
					//cout << "fr: " << fr << " ct: " << ct <<endl;
					// logfile <<ip << " " <<url << " first request plus quota is: " << fr << " the time of current request is: " << ct  << " time difference : " << fr-ct <<endl;
					if(fr > ct)
					{
						cout << buff << endl;
						// logfile << "banned, but inside quota, OK" <<endl;
					}
					else
					{
						cout << "302:http://192.168.1.201/denied.gif" << endl;
						// logfile << "banned, outside quota, ERR" <<endl;
					}
				}
				else
				{
					cout << buff << endl;
					// logfile << "not banned, OK" <<endl;
				}
				query.reset();
			}

			if(url == "exit")
			{
				break;
			}	
		}
		logfile.close();
		
	}
	else
	{
		// logfile << "connection fail" <<endl;
	}
	return 0;
}

```
So if I have implemented a solution what is my question?
Well it could be that I am at the wrong place for this kind of help but

A: 

As I said this code needs to be fast, could I get some feedback on my design. One thing of concern to me is that atm all requests to a banned site are logged, this could be a LOT of requests and while this table is emptied every day it could still get way to big. Maybe a solution that used update instead of insert and just updated the request time?

B: 

Code quality, have I made any mistakes with memory management etc.

C: [most important]

 How could I share this code with other people. I only wrote this because I couldn’t find free software which did it for me. What is the best way to get this into a form that other net admins can use? Ill need a lot of help with this I think as I have never used autoconfig before or anything like that.
-----------------------------------------------------

ORIGINAL POST:

I'm the network administrator of a fairly small network (<100 stations) and my work is generally just doing tech support for the staff here and managing services like samba mail etc. My boss recently approached me with a more difficult task however, she would like to limit the amount of time each staff member can access certain websites, allocating them a quota for example:

Bob can only view facebook for 10 minutes before 12:00, betweem 12:00 and 13:00 he gets another 30 minutes of quota, and then after 13:00 he gets another 10 minute sof quota.

Ideally this quota would be consumed only when a staff member was viewing a page but I don't think this is entirely possibly, perhaps  the quota would simply start counting down once the page is first accessed?

This system must be implemented for $0 using entirely free software and hardware we have sitting around the office.

Now I understand how to implement more basic filtering I could set up a transparent proxy using squid, which already supports user authentication, and then use something like Dansguardian for URL blacklisting. My questions is: is there free software which can handle this kind of time quota based control?

If there is not what would be the best DIY approach. I was thinking I could write a simple squid log parser of my own (in C or python or whatever) but this may be more work than is necessary. Is there perhaps a generic squid parsing tool which supports scripting that could do some of the work for me?

I could be totally off the mark and perhaps a proxy is not the best approach at all? I could add special logging rules to iptables and go from there but it seems to me that would be a lot more work.

Thanks in advance, capo.

---

### Post by Vegan on 2009-12-16
Long ago there was software for systems to time management that seems to have largely disappeared.

Such a level of control goes back to 70's era time share systems.

You could leverage a cron job to enable and disable access to some services.

You already found some URL black list tools, so that is part of the battle.

On the face of it, this is a hard task to envision with modern systems. I am only aware of black list blocking of sites.

---

### Post by craigp84 on 2009-12-16
Another approach would be to tell the staff, "hey, we'd like to let you have access to facebook etc. from work, but we don't want you to abuse the priveledge. As of today the following sites are unblocked..."

It's pretty simple to report on time each site has been used by each user (google for "squid squint" for an *ACE* tool for this). Have a look at some sample reports for a small / medium size network, it's presented as a very easy to navigate HTML site with list of users, (fairly accurate approximation of) how long they were browsing, what sites etc.

Just make sure you communicate up front that (because of AJAX calls etc.) even leaving the tab open in the background will cause their time viewing the site to be registered, so they really must close the browser window / tab for facebook or whatever when they're done.

---

### Post by craigp84 on 2009-12-16
In fact, now i think of it, i remember writing a wee perl script for a client which Squid would call / run via a pipe. Squid would supply the username on stdin, the script had to lookup an active directory domain and test whether the supplied username was a member of the "internet access" group.

This could be setup in combination with a squid ACL to only call into your script when certain sites were accessed, A blacklist of sites that must be authorised before access can be granted.

The script could maintain a scoreboard file of usernames, accumulated time today and time of the last request (use a cron job nightly to zero the scoreboard / start a fresh one).

If the last access time was < 4? mins ago, we assume the user was on the page all the time and update the running total of time spent browsing with the difference between that time and now.

Based on whether the user has exceeded their threshold, we then log the current access time and update the running total with the value we just tested (assuming it was less than ~4 mins, otherwise we can only assume they closed their browser or moved away from whatever site if there's been no HTTP calls to the site in over 4 mins -- especially true for ajax sites such as facebook). Or we just deny access.

I don't have access to that client's system from here just now, i've just set a reminder for when i get back in 4 hours or so and i'll post the relevant squid.conf snippets required and a copy of that perl script for testing group membership against Active Directory.

This is an interesting problem, time permitting (sorry paying customers come first :-) i'll be happy to help you work through this if you want.

Cheers

---

### Post by craigp84 on 2009-12-16
I said i wrote it, turns out it wasn't me, it's just a script i've customised, ah well :-)

```


#!/usr/bin/perl -w
#
# external_acl helper to Squid to verify NT Domain group
# membership using wbinfo
#
# This program is put in the public domain by Jerry Murdock 
# <jmurdock@itraktech.com>. It is distributed in the hope that it will
# be useful, but WITHOUT ANY WARRANTY; without even the implied warranty
# of MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.
#
# Author:
#   Jerry Murdock <jmurdock@itraktech.com>
#
# Version history:
#   2005-12-24 Guido Serassio <guido.serassio@acmeconsulting.it>
#               Fix for wbinfo from Samba 3.0.21
#
#   2005-06-28 Arno Streuli <astreuli@gmail.com>
#               Add multi group check
#
#   2002-07-05 Jerry Murdock <jmurdock@itraktech.com>
#		Initial release


# Disable output buffering
$|=1;           

sub debug {
	# Uncomment this to enable debugging
	print STDERR "@_\n";
}

#
# Check if a user belongs to a group
#
sub check {
        local @user = @_;
        $groupSID = `wbinfo -n "Internet Access" | cut -d" " -f1`;
        chop  $groupSID;
        $groupGID = `wbinfo -Y "$groupSID"`;
        chop $groupGID;
        $groups = `wbinfo -r \Q@user\E`;
	$groups =~ s/\n/ /g;
        &debug( "User: $user\nGIDs: $groups\nInetSID:   $groupSID\nInetGID:   $groupGID");
        return 'OK' if($groups =~ /$groupGID/);
        return 'ERR';
}

#
# Main loop
#
while (<STDIN>) {
        chop;
	&debug ("Got $_ from squid");
	($user = $_) =~ s/%20/ /;
	($user = $_) =~ s/"//g;
	# test for each group squid send in it's request
	$ans = &check($user);
	&debug ("Sending $ans to squid");
	print "$ans\n";
}


```

The relevant squid.conf entries to wire this up are -->

```
external_acl_type InternetGroupMembership children=5 %LOGIN /usr/bin/perl /usr/local/bin/wbinfo_group.pl
```

```
acl InternetUser external InternetGroupMembership
```

```
http_access allow all AuthorisedUsers InternetUser
```

Override that sub check just to always return ok for now, see how you get on wiring this up then we can do a proper check routine which does what you need.

---

### Post by redmk2 on 2009-12-16
An interresting time control app was written by Ubuntu user .nedberg  It's called ***timekpr***.  You can find it [**_[COLOR="DarkSlateGray"]here[/COLOR]_**]("https://launchpad.net/timekpr").

The development was sort of documented [**_[COLOR="DarkSlateGray"]here[/COLOR]_**]("http://ubuntuforums.org/showthread.php?t=1240877").

---

### Post by capo on 2009-12-16
> **redmk2 said:**
> An interresting time control app was written by Ubuntu user .nedberg  It's called ***timekpr***.  You can find it [**_[COLOR="DarkSlateGray"]here[/COLOR]_**]("https://launchpad.net/timekpr").

The development was sort of documented [**_[COLOR="DarkSlateGray"]here[/COLOR]_**]("http://ubuntuforums.org/showthread.php?t=1240877").

the staff all use windows though, i'm only running ubuntu on the servers.


@craigp84 -->

Thanks very much for your replies. I'm not much of a perl scripter but it's a C like language and as one of my lectuered once said, "once your a programmer if you need to learn a new language you can just read the reference in the bath".

I'm actually out of the office for a while because I need to visit Melbourne but when i get back to work ill investigate your suggestion. We don't actually have a windows domain so ill probably need to adjust your script a lot to use it, i was planning on using squid authentication as my method of identifying users, or worst case i could always use the host name of the pc.

---

### Post by BkkBonanza on 2009-12-17
Putting limits on certain sites is only going to restrict those that are clueless about proxy sites (and they'll soon hear about them around the coffee machine). If they are limited on Facebook they can just go to a proxy site and enter Facebook which will then give them access without logging the real address. 

You're better off having a whitelist plus other and track the other as always being non-work related. Whitelist is sites needed for work purposes. Assuming there's no proxies on the whitelist sites then non-work access gets counted. Why would you care if it's Facebook or Twitter or eBay etc.

This whole idea also assumes you'll block any ports you don't track, and that your staff aren't technically advanced.

---

### Post by capo on 2009-12-17
> **BkkBonaza said:**
> Putting limits on certain sites is only going to restrict those that are clueless about proxy sites (and they'll soon hear about them around the coffee machine). If they are limited on Facebook they can just go to a proxy site and enter Facebook which will then give them access without logging the real address. 

You're better off having a whitelist plus other and track the other as always being non-work related. Whitelist is sites needed for work purposes. Assuming there's no proxies on the whitelist sites then non-work access gets counted. Why would you care if it's Facebook or Twitter or eBay etc.

This whole idea also assumes you'll block any ports you don't track, and that your staff aren't technically advanced.

these aren't issues for which I need help for. I have set up school and office networks with proxies etc before, the only thing I am seeking advice on is specific software for time quota based control.

---

### Post by memilanuk on 2009-12-17
Until the IT dept. starts getting determined and starts blocking (and logging) any attempts to access known proxy sites...

---

### Post by BkkBonanza on 2009-12-17
I get it. You just want to do what the boss says. 
Even if it's a pointless waste of time.

---

### Post by BkkBonanza on 2009-12-17
> **memilanuk said:**
> Until the IT dept. starts getting determined and starts blocking (and logging) any attempts to access known proxy sites...

Way too much work. Just one web proxy list on google has 6,437 working proxies today (out of 34,924 listed) and they change all the time, and there's so many other lists on google as well.

Which is why I said the whitelist is a much better tactic than the blacklist. How many legit sites can people use for work purposes?

---

### Post by BkkBonanza on 2009-12-17
> **capo said:**
> Ideally this quota would be consumed only when a staff member was viewing a page but I don't think this is entirely possibly, perhaps  the quota would simply start counting down once the page is first accessed?

Thats' right. You can't even measure how long they view a page. Even trying means that they get one page hit before lunch, one during lunch, and one after lunch.

---

### Post by craigp84 on 2009-12-17
Maintaining a whitelist takes time. No seriously one client I used to do work for wanted to maintain their whitelist system, it was seeded with around 250,000 URLs (the list was also paid for and not cheap) and the exceptions required to the list were frequent, very high priority (sales or directors users), and my name was slightly tarnished by my inability to instantly update the whitelist.

That's where my first post solution of allow all websites (except maybe a phishing and advertising blocklist) and just audit for blatant violations of agreed policy, actually came from.

---

### Post by iponeverything on 2009-12-17
> **capo said:**
> I'm the network administrator of a fairly small network (<100 stations) and my work is generally just doing tech support for the staff here and managing services like samba mail etc. My boss recently approached me with a more difficult task however, she would like to limit the amount of time each staff member can access certain websites, allocating them a quota for example:

Bob can only view facebook for 10 minutes before 12:00, betweem 12:00 and 13:00 he gets another 30 minutes of quota, and then after 13:00 he gets another 10 minute sof quota.

Ideally this quota would be consumed only when a staff member was viewing a page but I don't think this is entirely possibly, perhaps  the quota would simply start counting down once the page is first accessed?

This system must be implemented for $0 using entirely free software and hardware we have sitting around the office.

Now I understand how to implement more basic filtering I could set up a transparent proxy using squid, which already supports user authentication, and then use something like Dansguardian for URL blacklisting. My questions is: is there free software which can handle this kind of time quota based control?

If there is not what would be the best DIY approach. I was thinking I could write a simple squid log parser of my own (in C or python or whatever) but this may be more work than is necessary. Is there perhaps a generic squid parsing tool which supports scripting that could do some of the work for me?

I could be totally off the mark and perhaps a proxy is not the best approach at all? I could add special logging rules to iptables and go from there but it seems to me that would be a lot more work.

Thanks in advance, capo.

I have to say that this seems like it would be a fun project.

What I would do is setup the captive portal software wifidog, so that anyone exiting the local LAN would have to authenticate. I have played with wifidog before with a captive audience of about 350 users. In its default incarnation is fairly limited, but I have found that the code is pretty easy to modify to suite your own needs. Once the a user is authenticated it is then possible to add the hooks for time quotas and other types of access limitations. 

Also, once you have the IP to user maped, ntop can give you very fine grained window into user Internet usage patterns.

Having your users authenticate for external access could have some beneficial effects in helping to alter bad habits.

---

### Post by memilanuk on 2009-12-17
Or they just use a service like OpenDNS, which has default filters like below (right alongside gambling, p0rn, etc.:

> 
Proxy/Anonymizer
Sites providing proxy bypass information or services. Also, sites that allow the user to surf the net anonymously, including sites that allow the user to send anonymous emails.

---

### Post by source.decay on 2009-12-17
I personally use the Leechblock Firefox plugin to block things after I spend too much time on them.  I know that is difficult to implement beyond a couple of computers and easy to work around by going to other browsers.

Just a thought.

---

### Post by capo on 2009-12-17
> **BkkBonaza said:**
> I get it. You just want to do what the boss says. 
Even if it's a pointless waste of time.

no not at all. What i am saying is that it's not the whitelist vs blacklist argument that I am seeking advice on. I'm seeking advice on software that can do time quota based access control, whether it be to websites on a blacklist or all websites not on a whitelist is not my concern atm, ill sort that out after i have decided to my time quota strategy and after discussing it with my boss (because maintaining whitelist does take a lot of time)

---

### Post by capo on 2010-01-12
updated original post considerably.

---

### Post by craigp84 on 2010-01-13
11 out of 10 capo, very well done!

In terms of sharing with other people, you have a couple of choices depending how much you want to use this as a learning experience.

For the ultimate, you could package the software for Debian / Ubuntu, it would mean changing your code slightly (logfile location stands out on my first read through, should be under /var/log/squid/), and it would mean a little legwork creating the package and ensuring the software installs under the squid user etc.

There's a few guides out there for this a quick google will turn up some decent well written step by steps.

If you dont want to waste too much time on it, you could create a google code project with a readme that describes what it does and how to build / install. That search indexed repository, coupled with the folks who've had exposure to this thread should mean that your project is turned up when someone else with your requirements comes along.

Congratulations again capo, very good job!

---

