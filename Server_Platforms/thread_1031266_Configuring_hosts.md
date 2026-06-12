---
title: "Configuring hosts"
date: 2009-01-05
forum: Server Platforms
---

### Post by happyhacker on 2009-01-05
Jolly confused here. I want to be able to use the server with two address ranges, 192.168.0.x and 192.168.1.x. The server is fixed at 192.168.0.2 and my router is 192.168.1.254.

The hosts file currently looks like:
127.0.0.1	localhost localhost
192.168.0.2	acdorserver1 acdorserver1
The following lines are desirable for IPv6 capable hosts
::1     localhost ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts

When I try to ping from the server anything on 192.168.1.x it fails. When I ping the server from any 192.168.1.x it works (in fact I have network access to the server files from my XP PC).

Can anyone suggest what files need changing to get the server to see the network? I cannot see why it does not auto find the PCs.

---

### Post by love477 on 2009-01-05
An Effective Way to live through the Harsh "winter"-Financial Depression for Foreign Trade Enterprises Recently I read a lot of articles about "winter is coming", in which many corporations are looking for "cotton-padded jackets" to defend the coldness. Some try to reduce the staff, some process to a brand operation, some shift to the domestic market, while there are some others even carry forward the "Shanzhai Spirit" (Shanzhai, like one of the senses of the word "ghotto" in English-connoting that something is kind of a poorly done, low-class approximation of another thing). So far, I would like to put forward some measures to live through the "winter" for foreign trade enterprises, especially for the CEOs of these companies.1. To build up your confidence. To our foreign trade members, confidence is the most important thing for what we need at present. It is just an instant phenomenon for the reduction of orders and the less of income. In a long way, our society is progressing and the human is also developing. If winter comes, can spring be far behind? We can not be taken in by those who shouted that "winter is hard to live". Otherwise we will be the substitutes of these people. Anyhow, I believe that so long as we can take some proper measures, we are sure to get through this depressed period. So long as we can persist in, a bright future will be drawing near. Who can run first in the winter, who can run faster.2. To save money. It's known to all that if we want to be able to survive in this harsh winter for a longer time, we have to try our best to save every penny. Here I would like to recommend Some suggestions for all my fellows.A. Reduction of personnel is not a wise way for saving money. I find that this way is always the first choice for most managers of foreign trade company. I do think this is quite irresponsible to our employees. These employees have done a lot of contributions and paid their sweat and toil for both the bosses and our companies. While now they are dismissed by our bosses when there's a financial crisis. I think this is not only irresponsible to our employees, but also irresponsible to our society.B. To own less "girlfriends" for most bosses. Most of the bosses usually affiliate with many girls except their own wife. And they always spend more time with these girls than to the employees in their company. My friend, the person who shares the burden and works with you at the moment is the one who sitting beside the computer and now still trying to explore new clients for you. (This suggestion is for some bosses who have a special habit.)C. To be care of the "tragedies of preventing winter" from the internet. The person who said that "winter is coming" or those who shouted that they can help you to "live through the winter" are usually the one who intended to get through by your money. Hereby, I'm suspicious of writing this article. Never believe it easily!Following are some recommendations to save money for my fellows.a. Check the office rent is higher or not. If an office in the middle of the downtown is just for reputation, you'd better change another cheaper one for a while at the moment. The saved money could be enough for several employees' salaries.b. Think about the effect of the foreign trade websites you have devoted a lot of money into. If it still didn't bring any profit for you, then you should think about to stop now. Usually the foreign trade promotion websites from internal demand much more money from their fellowmen than to foreigners. It is better to choose some foreign trade websites of high cost performance if you indeed need to get extensions from the websites.Following are some effective ways for your business extension.[http://www.okokchina.com/](http://www.okokchina.com/)[http://www.sz-wholesale.com/](http://www.sz-wholesale.com/)[http://www.oneinhundred.com/](http://www.oneinhundred.com/)[http://www.wellpromo.com/](http://www.wellpromo.com/)[http://www.mikesearch.com](http://www.mikesearch.com/) Make sure to be familiar with Skype. Try to use Skype for international phone call as far as possible. In addition, its searching function is also quite useful for finding clients.To join into some industry associations from Europe and the United States is also a good way. The cost for joining these associations is only around several hundred dollars. And these associations from abroad are indeed aiming to offer help to people. We can establish relations with customers through their help.3. To make money. This is the most difficult thing to do. Many articles from websites have offered a lot of ways to earn money. I would like also to suggest some of my ideas.A. Do not try online sales. Which I would like to emphasize here is that online sales will certainly earn some money, but it is very difficult to make money if that is foreign trade. You spend a lot of time and money to set up a website while there is no any sales volume at last. I think that foreign trade companies would better to find a good number of high-level sellers from Taobao (Asia's largest and most secure online trading platform). If you do want to do online sales, then please try to build good relations with these people so that they can be your online sales agents. While you are still acting as doing foreign trade which take charge the goods and the shipping only, and then leave the sales to them. In order to develop end market from abroad, you'd better spend more on Ebay. Try to convince some excellent sellers of Ebay from abroad to help you to sell. In a word, it's better to do your own things which you are good at it. You will feel suppressed if to face real consumers when you have used to foreign trade business.B. Do not develop emerging markets randomly. We all know that the cost for developing of a new customer is much higher than the cost of maintaining old customers. Your own products in the current foreign market have not yet done so deep penetration, it will cost more to develop new market while you are lack of money. Furthermore, financial crisis is global and its impact is widespread. Thus I would like to recommend that it's better to develop deeper and thorough in the existing market. Also we can try to build business relations with second-class distributors from abroad. We can find these customers through a lot of these foreign industry associations or whole-sale websites.

---

### Post by MJN on 2009-01-05
> **cantthinkofanickname said:**
> Jolly confused here. I want to be able to use the server with two address ranges, 192.168.0.x and 192.168.1.x. The server is fixed at 192.168.0.2 and my router is 192.168.1.254.You need to describe your setup better, in particular how your network is laid out. What is the subnet mask, i.e. are the 192.168.0.x and 192.168.1.x devices all in the same subnet?
 
> The hosts file currently looks like:
127.0.0.1 localhost localhost
192.168.0.2 acdorserver1 acdorserver1
 
Ignore the HOSTS files for now - they are not relevent to pinging devices with IP addresses. (However you might wish to remove the name duplications on each line as the second mention is superfluous)
 
> When I try to ping from the server anything on 192.168.1.x it fails. When I ping the server from any 192.168.1.x it works (in fact I have network access to the server files from my XP PC).Again, without knowing your network architecture/layout it is difficult to say what the problem is as we do not know where the packets are meant to be going (this is particularly relevent if your server has two network cards each sat on different networks).
 
Mathew

---

