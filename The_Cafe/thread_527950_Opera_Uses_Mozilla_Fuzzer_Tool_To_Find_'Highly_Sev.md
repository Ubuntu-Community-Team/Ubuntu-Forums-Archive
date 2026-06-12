---
title: "Opera Uses Mozilla Fuzzer Tool To Find 'Highly Severe' Bug"
date: 2007-08-17
forum: The Cafe
---

### Post by Dark Star on 2007-08-17
During the recent Black Hat security conference, the Mozilla Foundation publically released an open-source application security testing tool. Security fuzzers are software tools that test an application for problems like buffer overflows, format string vulnerabilities and error handling. Mozilla worked with Microsoft, Apple, and Opera before making their JavaScript fuzzer widely available in order to reduce the possibility that the tool might be used to expose vulnerabilities in the companies' browsers. Mozilla has been using it to detect and fix dozens of security bugs in Firefox, according to Window Snyder, head of Mozilla's product security.

The same security tool was used by Opera Software to find and patch what the company is calling a "highly severe" bug in its flagship browser. Opera noted in an advisory that the flaw could allow a hacker to execute code on the victim's machine. A virtual function call on an invalid pointer, which may reference data crafted by the attacker, can be used to execute arbitrary code. Opera Software released Opera V9.23 to fix the problem. The company publicly thanked Mozilla for providing them the JavaScript fuzzer.

News source: [InformationWeek]("http://www.informationweek.com/story/showArticle.jhtml?articleID=201800584&cid=RSSfeed_IWK_News")

---

