---
title: "Help with generating RSS"
date: 2008-04-27
forum: The Cafe
---

### Post by Zelut on 2008-04-27
I've been working on generating a simple RSS feed for a home grown website but I'm having issues on the feed-reader end.  When I first import the feed the feed-reader will show the content, but after the feed is updated the feed-reader still thinks it has already read that item and shows no new feeds.

I'm using python-cheetah to dynamically generate the rss.xml file, and all that it does is auto-fill the date and a one-line of content.  Below is what I have as my base rss.xml file.  This one file is simply rebuilt daily with a new date & new one-line of content.  Can anyone tell me how I can build this rss properly so that it can be updated nightly and the feed-reader will also recognize that it has changed/updated and show the client?

```
<?xml version="1.0" encoding="utf-8"?>
<rss version="2.0" xmlns:dc="http://purl.org/dc/elements/1.1/" xmlns:atom="http://www.w3.org/2005/Atom">
 <channel>
    <title>example.com website feed</title>
    <description>example.com</description>
    <link>http://example.com</link>
    <language>en</language>
    <pubDate>$date</pubDate> 
    <lastBuildDate>$date</lastBuildDate>
    <item>
        <title>example.com entry</title>
        <atom:link href="http://example.com" rel="self" type="application/rss+xml" />
        <description>
        $dynamically-generated-content-here
        </description>
        <pubDate>$date</pubDate>
    </item>
 </channel>
</rss>
```

---

