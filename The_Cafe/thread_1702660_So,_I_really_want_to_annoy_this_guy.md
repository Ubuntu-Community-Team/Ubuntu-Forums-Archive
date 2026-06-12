---
title: "So, I really want to annoy this guy"
date: 2011-03-08
forum: The Cafe
---

### Post by ki4jgt on 2011-03-08
This guy has setup a false login page, anyone who clicks on his profile is directed to a google sites page. I haven't worked in HTML in forever. Can someone remove the false login page so I can mess with this guy. He's got it where if you click anything on his profile, it automatically goes to the false page, even places which aren't links. So basically the whole page.

```


<!DOCTYPE HTML PUBLIC "-//W3C//DTD HTML 4.01//EN" "http://www.w3.org/TR/html4/strict.dtd"><html> 
<head> 
<script type="text/javascript">var mybTimer={cb:[]};mybTimer.headStart=new Date();window.onload=function(){mybTimer.windowLoad=new Date();};</script><title>myYearbook | scott apachy</title> 
<meta name="description" content="Meet new people, play fun games, free online dating, for high school, college, and every one!" /> 
<meta name="keywords" content="dating, free online dating, meet new people, social networking, high school, college" />  
<meta http-equiv="Content-Type" content="text/html; charset=iso-8859-1"> 
<meta http-equiv="Content-Script-Type" content="text/javascript"> 
<meta http-equiv="X-UA-Compatible" content="IE=EmulateIE7" /> 
 
<SCRIPT LANGUAGE="JavaScript"> 
<!-- 
 var gomez={ 
     gs: new Date().getTime(), 
     acctId:'12E899', 
     pgId:'Profile', 
     grpId:'' 
 }; 
 //--> 
 </SCRIPT> 
 <SCRIPT LANGUAGE="JavaScript"> 
<!-- 
var gomez=gomez?gomez:{};gomez.h3=function(d, s){for(var p in s){d[p]=s[p];}return d;};gomez.h3(gomez,{b3:function(r){if(r<=0)return false;return Math.random()<=r&&r;},b0:function(n){var c=document.cookie;var v=c.match(new RegExp(';[ ]*'+n+'=([^;]*)'));if(!v)v=c.match(new RegExp(n+'=([^;]*)'));if(v)return unescape(v[1]);return '';},c2:function(n,v,e,p,d,s){try{var t=this,a=location.hostname;var c=n+'='+escape(v)+(e?';expires='+e.toGMTString():'')+(p?';path='+p:';path=/')+(d?';domain='+d:';domain='+a)+(s?';secure':'');document.cookie=c;}catch(e){}},z0:function(n){var t=this;if(n){var s =t.b0("__g_c");if(!s)return '';var v=s.match(new RegExp(n+':([^|]*)'));if(v)return unescape(v[1]);return '';}else return '';},z1:function(n,m){var t=this;if(n){var s=t.b0("__g_c");if(s){if(s.indexOf(n+':')!=-1)s=s.replace(new RegExp('('+n+':[^|]*)'),n+':'+m);else s=s==' '?n+':'+m:s+'|'+n+':'+m;t.c2("__g_c",s);}else t.c2("__g_c",n+':'+m);};}});if(gomez.wrate){gomez.i0=gomez.z0('w');if(gomez.i0){gomez.runFlg=parseInt(gomez.i0)>0?true:false;}else if(gomez.b3(parseFloat(gomez.wrate))){gomez.runFlg=true;gomez.z1('w',1);}else{gomez.runFlg=false;gomez.z1('w',0);}}else if(gomez.wrate==undefined){gomez.runFlg=true;gomez.z1('w',1);}else{gomez.runFlg=false;gomez.z1('w',0);};if(gomez.runFlg){gomez.h1=function(v,d){return v?v:d};gomez.gs=gomez.h1(gomez.gs,new Date().getTime());gomez.acctId=gomez.h1(gomez.acctId,'');gomez.pgId=gomez.h1(gomez.pgId,'');gomez.grpId=gomez.h1(gomez.grpId, '');gomez.E=function(c){this.s=c;};gomez.E.prototype={g1:function(e){var t=gomez,i=t.g6(e);if(i)i.e=t.b5();}};gomez.L=function(m){this.a=m;};gomez.L.prototype={g2:function(m){var t=gomez,n=t.b5();var s=document.getElementsByTagName(m);var e=t.k;if(m=='script')e=t.j;if(m=='iframe')e=t.l;if(s){var l=s.length;for(var i=0;i<l;i++){var u=s[i].src||s[i].href;if(u &&!e[u]){var r =new gomez.E(e);t.grm[u]=r;e[u]=new t.c7(u, n);if(t.gIE&&m=='script')t.e2(s[i],'readystatechange',t.d2,false);else t.e2(s[i],'load',r.g1,false);}}}}};gomez.L.m=new Object;gomez.L.m['script']=new gomez.L();gomez.L.m['link']=new gomez.L();gomez.L.m['iframe']=new gomez.L();gomez.S=function(){var t=this,h=gomez.acctId+".r.axf8.net";t.x=location.protocol+'//'+h+'/mr/b.gif?';t.y=location.protocol+'//'+h+'/mr/a.gif?';};gomez.h2=function(){var t=this;t.gIE=false;t.f=new Object;t._h=0;t.j=new Object;t.k=new Object;t.l=new Object;t.m=location.href;t.p=-1;t.q=-1;t.t=new Array;t.u=new Array;t._w=false;t.gSfr=/KHTML|WebKit/i.test(navigator.userAgent);t.gc={'n':'c'};t.grm=new Object;t.b;t.a=0;t.d=false;t.x=false;t.s=new gomez.S;t._a=false;t.h6=false;};gomez.h3(gomez,{h5:function(u){try{var s=document.createElement('script');s.src=u;s.type='text/javascript';if(document.body)document.body.appendChild(s);else if(document.documentElement.getElementsByTagName('head')[0])document.documentElement.getElementsByTagName('head')[0].appendChild(s);}catch(e){}},a9:function(){var t=gomez,i=t.z0('a'),g=t.b0('__g_u');t.gc.h=t.z0('b');if(!t.gc.h)t.gc.h=1;t.z1('b',parseInt(t.gc.h)+1);if(i){t.a=parseInt(i);if(t.a==1){t._w=true;}else if(t.a==3){t.x=true;t._w=true;};t.d=true;t.gc.c=t.z0('c');t.gc.d=t.z0('d');t.gc.i=t.z0('e');t.gc.j=t.z0('f');if(t._w&&!t._a){t.h7();t._a=true;};}else {if(!t.gc.a)return;var s='v=1';t.c2('__g_u','1',new Date(t.gt()+1000));if(t.b0('__g_u')&&g&&g!='1'&&g.indexOf('NaN')==-1&&g.indexOf('undefined')==-1){s='v=0';var r=g.split('_');t.b2(parseInt(r[0]),parseInt(r[1])+1);if(r[4]&&r[4]!='0'&&t.gt()<parseInt(r[5])&&r[2]&&r[2]!='0'){t.b1(parseFloat(r[2]),parseFloat(r[3]),parseFloat(r[4]),parseInt(r[5]));return;};};t.h6=true;s=t.s.y+'a='+t.gc.a+'&'+s;if(t.gSfr)document.write("<scr"+"ipt src='"+s+"'"+"></scr"+"ipt>");else t.h5(s);};t.b=t.z0('g');},h7:function(){var t=gomez,u=t.tloc?t.tloc:location.protocol+'//'+t.acctId+'.t.axf8.net/js/gtag4.js';if(t.gSfr)document.write("<scr"+"ipt src='"+u+"'"+"></scr"+"ipt>");else t.h5(u);},b1:function(v,s,q,f){var t=this;if(t._a)return;if(t.b3(v)){t._w=true;t.a=1;var p=parseFloat(s/v);if(t.b3(p)){t.x=true;t.a=3;};};t.d=true;t.z1('a',t.a);t.z1('e',v);t.z1('f',s);t.gc.i=v;t.gc.j=s;t.h4(v,s,q,f);if(t._w){t.h7();t._a=true;};},b2:function(v,s){var t=this,f=new Date(t.gt()+946080000000),g=''+v+'_'+s;if(t._a)return;t.c2('__g_u',g,f);t.gc.c=v;t.gc.d=s;t.z1('c',v);t.z1('d',s);},h4:function(o,p,q,d){var t=this,f=new Date(t.gt()+946080000000),g=t.b0('__g_u');if(g&&g!='1'&&g.indexOf('NaN')==-1&&g.indexOf('undefined')==-1){var r=g.split('_'),s;if(d)s=d;else if(q&&q>=0)s=new Date(t.gt()+parseInt(q*86400000)).getTime();else{q=5;s=new Date(t.gt()+432000000).getTime();};g=''+r[0]+'_'+r[1]+'_'+o+'_'+p+'_'+q+'_'+s;t.c2('__g_u',g,f);};},gt:function(){return new Date().getTime()},b5:function(){return new Date().getTime()-gomez.gs},b6:function(){var t=gomez;t.p=t.b5();},f8:function(){var t=this;if(t.pollId1)clearInterval(t.pollId1);if(t.pollId2)clearInterval(t.pollId2);if(t.pollId3)clearInterval(t.pollId3);if(t.pollId4)clearInterval(t.pollId4);},b7:function(){var t =gomez;t.f8();t.q=t.b5();},c7:function(u, s){var t=this;t.m=u;t.s=s;},c8:function(){var t=gomez,n=t.b5(),l=document.images.length;if(l>t._h){for(var i=t._h;i<l;++i){var u=document.images[i].src;if(u){var r =new gomez.E(t.f);t.grm[u]=r;t.f[u]=new t.c7(u, n);t.e2(document.images[i],'load',t.c4,false);t.e2(document.images[i],'error',t.c5,false);t.e2(document.images[i],'abort',t.c6,false);}}}t._h=l;},c4:function(e){var t=gomez,i=t.g6(e);if(i)i.e=t.b5();},c5:function(e){var t=gomez,i=t.g6(e);if(i){i.e=t.b5();i.b=1;}},c6:function(e){var t=gomez,i=t.g6(e);if(i)i.a=t.b5();},g6:function(e){var t=gomez,e=window.event?window.event:e,a=t.d8(e),i;if(t.grm[a.src||a.href]&&t.grm[a.src||a.href].s)i=t.grm[a.src||a.href].s[a.src||a.href];return i;},d2:function(){var t=gomez;var e=window.event?window.event:e,s=t.d8(e);if(s.readyState=='loaded'||s.readyState=='complete'){var o=t.j[s.src];if(o)o.e=t.b5();}},setPair:function(name,value){var t=this;t.t[t.t.length]={'n':'p','a':name,'b':value};},nameEvent:function(n){var t=this;t.f6(n,1);},startInterval:function(n){var t=this;t.f6(n,2,1);},endInterval:function(n){var t=this;t.f6(n,2,2);},f6:function(n,p,b){if(n&&n.length>20)n=n.substring(0,20);var t=this,f=t.u;f[f.length]={'n':'a','a':n,'b':t.b5(),'e':p,'f':b};},d8:function(e){if(gomez.gIE)return e.srcElement||{};else return e.currentTarget||e.target||{};},e2:function(e,p,f,c){var n='on'+p;if(e.addEventListener)e.addEventListener(p,f,c);else if(e.attachEvent)e.attachEvent(n, f);else{var x=e[n];if(typeof e[n]!='function')e[n]=f;else e[n]=function(a){x(a);f(a);};}},i1:function(){var d =window.document, done=false,i2=function (){if(!done){done=true;gomez.b6();gomez.a9();}};(function (){try{d.documentElement.doScroll('left');}catch(e){setTimeout(arguments.callee, 50);return;}i2();})();d.onreadystatechange=function(){if(d.readyState=='complete'){d.onreadystatechange=null;i2();}};},g7:function(){try{var t=gomez;t.gc.a=t.acctId;/*@cc_on t.gIE=true;@*/if(t.gIE){t.i1();window.attachEvent('onload', t.b7);}else if(t.gSfr){var m=setInterval(function(){if(/loaded|complete/.test(document.readyState)){clearInterval(m);delete m;t.b6();t.b7();}}, 10);}else if(window.addEventListener){window.addEventListener('DOMContentLoaded', t.b6, false);window.addEventListener('load', t.b7, false);}else return;t.c8();t.pollId1=setInterval(t.c8, 1);gomez.L.m['link'].g2('link');t.pollId3=setInterval("gomez.L.m['link'].g2('link')", 1);gomez.L.m['iframe'].g2('iframe');t.pollId4=setInterval("gomez.L.m['iframe'].g2('iframe')", 1);if(!t.gIE)t.a9();}catch(e){return;}}});gomez.h2();gomez.g7();}
//--> 
</SCRIPT> 
 
<link href="http://assets.mybcdna.com/css/sitecss2.css?63644" rel="stylesheet" type="text/css"> 
<link rel="stylesheet" href="http://assets.mybcdna.com/css/apps/DragonDrop.css?63644" type="text/css"> 
<link rel="stylesheet" href="http://assets.mybcdna.com/css/apps/Navbar.css?63644" type="text/css"> 
<link rel="stylesheet" href="http://assets.mybcdna.com/css/apps/VIP/VIPGift.css?63644" type="text/css"> 
<link href="http://assets.mybcdna.com/css/apps/Causes/CausesBadges.css?63644" rel="stylesheet" type="text/css"> 
<link href="http://assets.mybcdna.com/css/apps/ActionIcons.css?63644" rel="stylesheet" type="text/css"> 
<link rel="stylesheet" href="http://assets.mybcdna.com/css/apps/SuggestionBox.css?63644" type="text/css"> 
<link rel="shortcut icon" href="http://assets.mybcdna.com//favicon.ico" type="image/ico"> 
<link rel="stylesheet" href="http://assets.myyearbook.com/nerve/css/nerve.css?63644" type="text/css"> 
<script type="text/javascript" src="http://assets.mybcdna.com/JavaScript/apps/jQuery-1.2.6/jQuery.js?63644"></script> 
<script type="text/javascript">mybTimer.readyStart=new Date();</script><script type="text/javascript" src="http://assets.mybcdna.com/JavaScript/apps/jQuery-1.2.6/Plugins/myYearbook.DragonDrop/myYearbook.DragonDrop.js?63644"></script> 
<script type="text/javascript" src="http://assets.mybcdna.com/JavaScript/apps/jQuery-1.2.6/Plugins/myYearbook.ColorPicker/myYearbook.ColorPicker.js?63644"></script> 
<script type="text/javascript" src="http://assets.mybcdna.com/JavaScript/apps/Navbar.js?63644"></script> 
<script type="text/javascript" src="http://assets.mybcdna.com/JavaScript/apps/VIP/VIPGift.js?63644"></script> 
<script type="text/javascript" src="http://assets.mybcdna.com/JavaScript/apps/swfobject/swfobject.js?63644"></script> 
<script type="text/javascript" src="http://assets.mybcdna.com/JavaScript/common.js?63644"></script> 
<script type="text/javascript" src="http://assets.mybcdna.com/JavaScript/apps/SuggestionBox.js?63644"></script> 
<script type="text/javascript" src="http://assets.myyearbook.com/nerve/js/nerve.js?63644"></script> 
<script type="text/javascript"> 
  $(document).ready( function(){
    nerve.init( 'nerve.myyearbook.com', 80, '/nerve', {page: document.location.href});
    nerve.notificationManager.setLegacy( );
  });
</script> 
<script type="text/javascript">if(typeof MyYearbook=="undefined"){MyYearbook={}};MyYearbook.Member={"id":26701411,"isAdministrator":false,"isLoggedIn":true,"photoSquare":"thumb_userimages/square/2010/11/06/09/thm_phpbzMbZj_50_0_350_300.jpg","photoSquareMini":"thumb_userimages/square-mini/2010/11/06/09/thm_phpbzMbZj_50_0_350_300.jpg"};</script> 
<meta name="Robots" content="NOARCHIVE"> 
<meta name="Googlebot" content="NOARCHIVE"> 
<link rel="stylesheet" href="http://assets.mybcdna.com//css/apps/ShareContent.css?63644" type="text/css"> 
<link rel="stylesheet" href="http://assets.mybcdna.com//css/apps/Feed/FeedProfile.css?63644" type="text/css"> 
<link rel="stylesheet" href="http://assets.mybcdna.com//css/apps/Comments/CommentsCondensedProfile.css?63644" type="text/css"> 
<link rel="stylesheet" href="http://assets.mybcdna.com//css/apps/AskMe/AskMe.css?63644" type="text/css"> 
<link rel="stylesheet" href="http://assets.mybcdna.com//css/apps/Friends/FriendsSelector.css?63644" type="text/css"> 
<link rel="stylesheet" href="http://assets.mybcdna.com//css/stickers/reportStickersPopUp.css?63644" type="text/css"> 
<link rel="stylesheet" href="http://assets.mybcdna.com//css/Profile.css?63644" type="text/css"> 
<link rel="stylesheet" href="http://assets.mybcdna.com//css/apps/VIP/VIPBadges.css?63644" type="text/css"> 
 
<script type="text/javascript" src="http://assets.mybcdna.com/JavaScript//apps/ShareContent.js?63644"></script> 
<script type="text/javascript" src="http://assets.mybcdna.com/JavaScript//apps/TruthGame/TruthGame.js?63644"></script> 
<script type="text/javascript" src="http://assets.mybcdna.com/JavaScript//apps/Polls/ChatterPolls.js?63644"></script> 
<script type="text/javascript" src="http://assets.mybcdna.com/JavaScript//apps/AskMe/AskMe.js?63644"></script> 
<script type="text/javascript" src="http://assets.mybcdna.com/JavaScript//apps/Friends/FriendsSelector.js?63644"></script> 
<script type="text/javascript" src="http://assets.mybcdna.com/JavaScript//Profile.js?63644"></script> 
<script type="text/javascript">var stok="394900f694cadf226981eb43d1f43927";window.gaVars=jQuery.extend(window.gaVars,[]);window.gaVars[1]={"name":"gender","value":"male"};window.gaVars[2]={"name":"age","value":22};TOKEN = '394900f694cadf226981eb43d1f43927';</script> 
 
 
<script type="text/javascript">mybTimer.headEnd=new Date();</script></head> 
<body id="Profile" class="ProfileView" style="text-align:center;"> 
	<table id="maincontainer" cellpadding="0" cellspacing="0"  class="profiletable"  style="margin-left:auto;margin-right:auto;"><tr><td id="firsttd"> 
              <script type="text/javascript"> 
var cachebuster = "63644";
BATCAT_URL = "http://content1.myyearbook.com/battle_categories";
CONTEST_URL = "http://content1.myyearbook.com";
CSS_URL = "http://assets.mybcdna.com/css/";
IMAGE_URL = "http://assets.mybcdna.com/";
JAVASCRIPT_URL = "http://assets.mybcdna.com/JavaScript/";
LOCKER_URL = "http://locker.myyearbook.com";
PHOTO_URL = "http://content1.myyearbook.com";
SITEURL = SITE_URL = "http://www.myyearbook.com/";
MOVIES_URL = "http://movies.myyearbook.com/";
TOYS_URL = "http://toys.myyearbook.com";
IM_DOMAIN = "myyearbook.com";
IM_NAME = "myyearbook";
VIP_URL = "http://vip.myyearbook.com/";
MyYearbook.URLs = {"TV":"http://tv.myyearbook.com/","CPA":"http://cpa.myyearbook.com/","ssl":"https://ssl.myyearbook.com/","Games":"http://games.myyearbook.com","Causes":"http://causes.myyearbook.com/","www":"http://www.myyearbook.com/","VIP":"http://vip.myyearbook.com/","Home":"http://home.myyearbook.com/","BlindDate":"http://blinddate.myyearbook.com/","Chatter":"http://chatter.myyearbook.com/","Live":"http://live.myyearbook.com/","Platform":"http://platform.myyearbook.com/"};
MyYearbook.currentServiceName = 'www';
tabMenu=new Array();
 
$(document).ready(function(){
  if ( $('#cpaPromo').length > 0 )
  {
    $.ajax({
      type:'get',
      dataType:'json',
      url:'/apps/cpa/ajax',
      success:function(res)
      {
        $('#cpaPromo').removeClass('cpaLoading').html(res.markup);
        CPA.Init();
      }
    });
  }
});
</script> 
 
<script type="text/javascript" src="http://assets.mybcdna.com/JavaScript/apps/IM/IM.js?63644"></script> 
 
<div id="header" class="gradientSprite"> 
  <div class="headerSprite" id="logo" data-id="home"> 
    <a href="/">myYearbook.com</a> 
  </div> 
  <ul id="navLinks"> 
    <li data-id="home"><a href="/">Home</a></li> 
    <li class="profileMenu" data-id="profile"><a href="http://www.myyearbook.com/?mysession=cmVnaXN0cmF0aW9uX3Byb2ZpbGUmdXNlcmlkPTI2NzAxNDEx">Profile</a></li> 
    <li id="profileIcon"></li> 
    <li data-id="friends"><a href="http://friends.myyearbook.com/">Friends</a></li> 
    <li class="messages" data-id="messages"><a href="http://messages.myyearbook.com/">Messages</a></li> 
            <li id="navLunchMoney" data-id="lunchmoney"><a href="/?mysession=bHVuY2htb25leV9teXNvY2s="><span class="lmSymbol">L$</span><span class="lmValue">25,916</span></a></li> 
      </ul> 
  <div id="profileIconOverlay"></div> 
  <div id="headerSearch"> 
    <form action="/?mysession=c2VhcmNoX3NlYXJjaF9yZXN1bHRzX2FkdmFuY2Vk" method="post" name="quicksearch" id="quickSearch"> 
      <ul> 
        <li id="searchIcon" class="headerSprite"></li> 
        <li class="searchInput"> 
          <input id="quickSearchBox" class="searchBox" type="text" value="Quick Name Search" name="s_name" maxlength="32" data-id="quicksearch" /> 
          <input type="hidden" value="1" name="quicknamesearch"/> 
        </li> 
        <li id="reportIcon" class="headerSprite" data-id="reportabuse"><a href="/?mysession=bGlzdGluZ19ib2d1cyZjdXJyZW50X2JhdHRsZV9pZD0mcGljaWQ9JmNvbnRlc3Rmb3I9JnVzZXJpZD0yNjY5NDcyMQ==">Report</a></li> 
      </ul> 
    </form> 
    <div id="searchIconOverlay"></div> 
  </div> 
  <ul id="siteSearchNav"> 
        <li data-id="settings"><a href="/?mysession=cmVnaXN0cmF0aW9uX3NldHRpbmdzX3ByaXZhY3k=">Settings</a></li> 
    <li data-id="logout"><a href="/?mysession=cmVnaXN0cmF0aW9uX2xvZ291dA==">Logout</a></li> 
      </ul> 
  <ul id="siteSearchMenu"> 
    <li data-id="browsepeople"><a href="/?mysession=c2VhcmNoX3NlYXJjaF9yZXN1bHRzX2FkdmFuY2VkJnNlYXJjaHR5cGU9QkFTSUMmZmlyc3RwYWdlPXk=">Browse People</a></li> 
    <li data-id="namesearch"><a href="/?mysession=c2VhcmNoX3NlYXJjaCZzZWFyY2h0eXBlPU5BTUU=">Name Search</a></li> 
    <li data-id="emailsearch"><a href="/?mysession=c2VhcmNoX3NlYXJjaCZzZWFyY2h0eXBlPUVNQUlM">Email Search</a></li> 
    <li data-id="schoolsearch"><a href="/?mysession=c2VhcmNoX3NlYXJjaCZzZWFyY2h0eXBlPVlFQVJCT09L">School Search</a></li> 
    <li data-id="advancedsearch"><a href="/?mysession=c2VhcmNoX3NlYXJjaF9yZXN1bHRzX2FkdmFuY2VkJnNlYXJjaHR5cGU9QURWQU5DRUQmZmlyc3RwYWdlPXk=">Advanced Search</a></li> 
  </ul> 
  <ul id="profileMenu"> 
    <li data-id="myphotos"><a href="/?mysession=cmVnaXN0cmF0aW9uX215cGljdHVyZXM=">My Photos</a></li> 
    <li data-id="myautographs"><a href="/?mysession=bGlzdGluZ192aWV3X2F1dG9ncmFwaHM=">My Autographs</a></li> 
    <li data-id="mystickers"><a href="/?mysession=c3RpY2tlcnNfdmlld2FsbHN0aWNrZXJz=">My Stickers</a></li> 
    <li data-id="myflirts"><a href="/?mysession=ZmxpcnRzX3ZpZXdGbGlydHM=">My Flirts</a></li> 
    <li data-id="mygifts"><a href="/apps/gifts/premium/my">My Gifts</a></li> 
    <li data-id="myviews"><a href="/apps/search/profileviews/">My Profile Views</a></li> 
    <li data-id="whateveriwant"><a href="/?mysession=cmVnaXN0cmF0aW9uX3doYXRldmVyaXdhbnQ=">Whatever I Want</a></li> 
    <li data-id="myvideos"><a href="/?mysession=dmlkZW9fdXNlcg==">My Videos</a></li> 
    <li data-id="myblog"><a href="/?mysession=YmxvZ3NfYmxvZw==">My Blog</a></li> 
  </ul> 
</div> 
<ul id="navbar"><li id="navbar_morefun"><div class="text">More Fun</div></li><li class="navbar_live" data-id="live"><a href="http://live.myyearbook.com/?ref=navbar">Live</a></li><li class="navbar_match" data-id="match"><a href="http://www.myyearbook.com/apps/match">Match</a></li><li class="navbar_blinddate" data-id="blinddate"><a href="http://blinddate.myyearbook.com/">Blind Date</a></li><li class="navbar_owned" data-id="owned"><a href="http://www.myyearbook.com/apps/owned/browse">Owned!</a></li><li class="navbar_askme" data-id="askme"><a href="http://chatter.myyearbook.com/askMe">Ask Me</a></li><li class="navbar_games" data-id="games"><a href="http://games.myyearbook.com/">Games</a></li><li class="navbar_causes" data-id="causes"><a href="http://causes.myyearbook.com/">Causes</a></li><li class="navbar_battles" data-id="battles"><a href="http://www.myyearbook.com/?mysession=YmF0dGxlc192b3RlX2JhdHRsZQ==">Battles</a></li><li class="navbar_mymag" data-id="mymag"><a href="http://www.myyearbook.com/?mysession=bWFnX2luZGV4">myMag</a></li><li class="navbar_chatter" data-id="chatter"><a href="http://chatter.myyearbook.com/">Chatter</a></li></ul> 
    
            
  <div id="contentarea" style="text-align:left;"> 
         <script type="text/javascript" src="http://assets.mybcdna.com/JavaScript/flashdetect.js"></script> 
<script type="text/javascript" src="http://assets.mybcdna.com/JavaScript/ajax.class.js"></script> 
<script type="text/javascript" src="http://assets.mybcdna.com/JavaScript/class.video.js?15303"></script> 
<script type="text/javascript" src="http://assets.mybcdna.com/JavaScript/class.dragondrop.js"></script> 
<script type="text/javascript" src="http://assets.mybcdna.com/JavaScript/jQuery/Plugins/hovertip.js"></script> 
<script type="text/javascript" src="http://assets.mybcdna.com/JavaScript/apps/Comments/CommentsCondensed.js?63644"></script> 
<script type="text/javascript" src="http://assets.mybcdna.com/JavaScript/apps/Feed/Feed.js?63644"></script> 
<script type="text/javascript" src="http://assets.mybcdna.com/JavaScript/apps/Feed/FeedVideo.js?63644"></script> 
<script type="text/javascript" src="http://assets.mybcdna.com/JavaScript/apps/Status/Status.js?63644"></script> 
<script type="text/javascript" src="http://assets.mybcdna.com/JavaScript/apps/Tools/InputCountdown.js?63644"></script> 
<script type="text/javascript" src="http://assets.mybcdna.com/JavaScript/apps/MemberInterest/MemberInterest.js?63644"></script> 
<script type="text/javascript" src="http://assets.mybcdna.com/JavaScript/apps/MemberReport/MemberReport.js?63644"></script> 
<script type="text/javascript" src="http://assets.mybcdna.com/JavaScript/apps/Photos/PhotoHandler.js?63644"></script> 
<script type="text/javascript" src="http://assets.mybcdna.com/JavaScript/apps/myYearbook.js?63644"></script> 
<script type="text/javascript" src="http://assets.mybcdna.com/JavaScript/apps/VIP/VIP.js?63644"></script> 
<script type="text/javascript" src="http://assets.mybcdna.com/JavaScript/apps/Connect/ConnectLauncher.js?63644"></script> 
<script src="http://assets.mybcdna.com/JavaScript/apps/jQuery-1.2.6/Plugins/myYearbook.ActionIcons/myYearbook.ActionIcons.js?63644" type="text/javascript"></script> 
<script src="http://assets.mybcdna.com/JavaScript/apps/jQuery-1.2.6/Plugins/myYearbook.FileUploader/myYearbook.FileUploader.js?63644" type="text/javascript"></script> 
<script src="http://assets.mybcdna.com/JavaScript/apps/Pagination/Paginator.js?63644" type="text/javascript"></script> 
<script src="http://assets.mybcdna.com/JavaScript/apps/Requests/RequestsSender.js?63644" type="text/javascript"></script> 
<link rel="stylesheet" type="text/css" href="http://assets.mybcdna.com/css/apps/Pagination/Paginator.css?63644"></link> 
<link rel="stylesheet" type="text/css" href="http://assets.mybcdna.com/css/apps/Requests/Requests.css?63644"></link> 
<link rel="stylesheet" type="text/css" href="http://assets.mybcdna.com/css/apps/VIP/VIP.css?63644"></link> 
<style type="text/css" title="customcss" class="customcss">.tabfrmbrd { filter: alpha(opacity=100); opacity: 1; -khtml-opacity: 1; -moz-opacity: 1;}</style> 
 <input type="hidden" id="userid" value="26694721"> 
 <input type="hidden" id="sessuserid" value="26701411"> 
<script type="text/javascript"> 
var tok = "394900f694cadf226981eb43d1f43927";
var pageCaptcha = false;
 
fallimage='';
 
if(fallimage!=''){
  window.onload=function(){
    Profile.initFallingImage();
    fallingboolean=1;
    Profile.fall(1);
  }
}
else{
  fallingboolean=0;
}
 
 
var ownedIdx = -1;
$(document).ready( function() {
  window.setTimeout( hovertipInit, 1 );
 
    $.ajax({url:SITEURL+'/ajax/profile/viewprofile.php',dataType:'text',cache:false});
 
 
});
 
 
</script> 
<input id="token" name="token" type="hidden" value="394900f694cadf226981eb43d1f43927"> 
<div id="profilecontent"> 
 
        
    
    
  
<div id="subcontainer"> 
<table cellspacing="0" cellpadding="10" class="normaltext" style="width:100%"><tr> 
<td id="leftcolumn" style="vertical-align:top"> 
  <div id="picbox" class="divleft" style="text-align:center;" class="pad5">    <table width="90" cellspacing="0" cellpadding="0" class="imgtbl" style="margin:auto;"> 
      <tr> 
        <td class="profilePicBox"> 
                      <a href="/?mysession=cmVnaXN0cmF0aW9uX3BpY3R1cmVzJnVzZXJpZD0yNjY5NDcyMQ=="> 
              <img id="defaultProfilePhoto" src="http://content1.myyearbook.com/thumb_userimages/2011/03/07/09/thm_phpqVLHY5.jpg" alt=""> 
            </a> 
                            </td> 
      </tr> 
    </table> 
 
                  
  </div> 
            <div class="tabfrmbrd sectbg2 divleft" style="text-align:center;padding:7px 0px; width: 346px; margin-top: 10px;"> 
        <a href="#" class="normaltextlink friendsPop" style="margin:5px;font-weight:bold;font-size:18px;" onclick="return false;"> 
                      Add to Friends
                  </a> 
      </div> 
      
        &nbsp;<br> 
  <div id="profileQuickMessage" class="divleft"> 
    <textarea id="profileQMBody" class="textboxInstructionOverlay">Type me a quick message...</textarea> 
    <span id="profileQMButtonFix">&nbsp;</span> 
    <div id="profileQMBtnContainer"><button id="profileQMSend"> Send </button></div> 
  </div> 
  
  &nbsp;
    <div id="divActions" class="tabfrmbrd sectbg1 divleft"> 
    <table class="actionList" style="margin:0px 10px;text-align:center;" cellpadding="0" cellspacing="0"> 
      <tr> 
        <td><a title="Send Him a Message" class="btnActionIcon aiMessage messagePop" href="#"></a></td> 
        <td><a title="Give a Gift" class="btnActionIcon aiGift giftPop" href="#"></a></td> 
        <td><a title="Give Him a Gold Star" class="btnActionIcon aiGoldStar goldStarPop" href="#"></a></td> 
        <td><a title="Stick Him" class="btnActionIcon aiSticker stickerPop" href="#"></a></td> 
        <td><a title="Send Flirt to Him" class="btnActionIcon aiFlirt flirtPop" href="#"></a></td> 
        <td><a title="Secretly Admire Him" class="btnActionIcon aiAdmire admirePop" href="#"></a></td> 
        <td><a title="Give Him a High Five" class="btnActionIcon aiHighFive highFivePop" href="#"></a></td> 
        <td><a title="Battle Him" class="btnActionIcon aiBattle" href="/?mysession=YmF0dGxlc19jcmVhdGViYXR0bGUmcj1wcm9maWxlJnJpZ2h0X3VzZXI9MjY2OTQ3MjE="></a></td> 
      </tr> 
    </table> 
    <div class="clr" style="border-top:1px solid #ccc;padding:7px 0px;margin:0px 10px;"> 
      <span style="float:left;"><img src="http://assets.mybcdna.com/friendfinder/owned_cash_icon_sm.gif" alt="" style="vertical-align:middle;"> <span data-vip-product-type="lunchmoney" class="pseudolink normaltextlink" onclick="productBootloader( 'lunchmoney', vipData );" style="vertical-align:middle;">Gift Lunch Money!</span></span> 
      <span style="float:right;"><img src="http://assets.mybcdna.com/images/vip/vip_card_mini_gray.png" alt="" style="vertical-align:middle;"> <span data-vip-product-type="vip_membership" class="pseudolink normaltextlink" onclick="productBootloader( 'vip_membership', vipData );" style="vertical-align:middle;">Gift the VIP Club!</span></span> 
      <div class="clr"></div> 
    </div> 
  </div>    
    &nbsp;<br> 
  <div id="memorableLinkBox" class="tabfrmbrd divleft"> 
    <div id="memorableLink" class="sectbg1"> 
    <div style="padding:7px 14px;"> 
      <div><a href="#" class="normaltextlinkbold" style="float:right;" onclick="Profile.bookmarksite('myYearbook | scott apachy', 'http://www.myyearbook.com/?mysession=cmVnaXN0cmF0aW9uX3Byb2ZpbGUmdXNlcmlkPTI2Njk0NzIx');return false;">Bookmark</a><b>scott's Profile Link:</b></div> 
      <input type="text" class="textbox" id="memorableLinkText" name="memorableLinkText" style="width:315px;" onclick="copyText('memorableLinkText');" value="http://www.myyearbook.com/?mysession=cmVnaXN0cmF0aW9uX3Byb2ZpbGUmdXNlcmlkPTI2Njk0NzIx" readonly="readonly"> 
      <div id="memorableLinkText_msg" class="customizeLinkCopy"></div> 
          </div> 
  </div> 
  </div> 
  
    <span>&nbsp;<br></span> 
  <div id="divGifts" class="tabfrmbrd divleft"> 
    <div class="secthead"> 
              <a href="/apps/gifts/premium/my/26694721" class="sectlink" style="float:right">[View All]</a> 
            Gifts
    </div> 
    <div class="sectcontbrd sectbg1"> 
      <div id="vipBanner" class="sectbg2"> 
                <div class="giftBox">Loading...</div> 
              </div> 
      <script type="text/javascript">VIPGiftProfile.initBanner();</script> 
    <table cellspacing="0" cellpadding="0" style="width:100%;text-align:center;"> 
      <tr> 
        <td> 
                <div id="premiumGiftsContainer"> 
  <div id="giftsProfileArea" class="sectbg2"> 
    <span class="hidden viewedUser">26694721</span> 
    <div class="pgTextArea"> 
      <div class="normaltextbold">scott has 2 Premium Gifts</div> 
      <div class="pgTextArea normaltext"> 
                    Click on a gift to view it!
                  </div> 
    </div> 
    <div class="clear"> </div> 
    <div style="float:left;width:100%" class="profileGiftsContainer"> 
      <div style="float:left;" class="profileGiftArea pgPadLeft"> 
        <div class="profilePGImageArea"> 
          <img alt="Gift Image" class="profilePGImage unwrapPG" src="http://assets.mybcdna.com/images/PremiumGifts/wolf/small.jpg"/> 
          <span class="memberGiftID hidden">202998935</span> 
          <span class="offset hidden">0</span> 
        </div> 
        <span class="normaltext">From: </span> 
        <a class="normaltextlink" href="http://www.myyearbook.com/?mysession=cmVnaXN0cmF0aW9uX3Byb2ZpbGUmdXNlcmlkPTE2ODEyODQy">Jasmine</a> 
      </div> 
      <div style="float:left;" class="profileGiftArea pgPadLeft"> 
        <div class="profilePGImageArea"> 
          <img alt="Gift Image" class="profilePGImage unwrapPG" src="http://assets.mybcdna.com/images/PremiumGifts/warp_speed/small.jpg"/> 
          <span class="memberGiftID hidden">201789247</span> 
          <span class="offset hidden">1</span> 
        </div> 
        <span class="normaltext">From: </span> 
        <a class="normaltextlink" href="http://www.myyearbook.com/?mysession=cmVnaXN0cmF0aW9uX3Byb2ZpbGUmdXNlcmlkPTI1ODkyOTIy">casey</a> 
      </div> 
      <div class="clear"> </div> 
      <span class="viewedUser hidden">26694721</span> 
    </div> 
    <div class="clear"> </div> 
    <div style="width:100%" class="pgTextAreaBottom"> 
      <a href="#" class="normaltextlink giftPop">Give scott a Premium Gift!</a> 
    </div> 
  </div> 
</div> 
 
                <div class="premiumGiftsLoading hidden"> 
          Loading Premium Gifts...<br><img src="http://assets.mybcdna.com/images/loading/99cc66-ffffff-circle_ball.gif" /> 
        </div> 
        </td> 
      </tr> 
    </table> 
        <table id="displayGiftArea" cellspacing="5" cellpadding="0" style="width:100%;text-align:center;"> 
      <tr> 
              <td style="width:33%;"> 
        <img width="64" height="64" src="http://assets.mybcdna.com/gifts/food/CupCake.jpg" alt=""><br> 
                <span class="normaltext">From: </span><a href="/?mysession=cmVnaXN0cmF0aW9uX3Byb2ZpbGUmdXNlcmlkPTIwMTk3OTcx" class="normaltextlink">Britney</a> 
                </td> 
                      <td style="width:33%;"> 
        <img width="64" height="64" src="http://assets.mybcdna.com/gifts/music/Headphones.jpg" alt=""><br> 
                <span class="normaltext">From: </span><a href="/?mysession=cmVnaXN0cmF0aW9uX3Byb2ZpbGUmdXNlcmlkPTg5Nzk4NzI=" class="normaltextlink">Robert (NBL)</a> 
                </td> 
                      <td style="width:33%;"> 
        <img width="64" height="64" src="http://assets.mybcdna.com/gifts/random_items/killer_rabbit_slippers.jpg" alt=""><br> 
                <span class="normaltext">From: </span><a href="/?mysession=cmVnaXN0cmF0aW9uX3Byb2ZpbGUmdXNlcmlkPTMwNjk1NDk2" class="normaltextlink">leseanna</a> 
                </td> 
        </tr><tr>              <td style="width:33%;"> 
        <img width="64" height="64" src="http://assets.mybcdna.com/gifts/stuffed_animals/monkey.jpg" alt=""><br> 
                <span class="normaltext">From: </span><a href="/?mysession=cmVnaXN0cmF0aW9uX3Byb2ZpbGUmdXNlcmlkPTk5MzA4NTE=" class="normaltextlink">Alexes[Add Me]</a> 
                </td> 
                      <td style="width:33%;"> 
        <img width="64" height="64" src="http://assets.mybcdna.com/gifts/naughty/catwoman_outfit.jpg" alt=""><br> 
                <span class="normaltext">From: </span><a href="/?mysession=cmVnaXN0cmF0aW9uX3Byb2ZpbGUmdXNlcmlkPTI3MzAwNzU1" class="normaltextlink">&#9829;&#9829;LIL C~MF</a> 
                </td> 
                      <td style="width:33%;"> 
        <img width="64" height="64" src="http://assets.mybcdna.com/gifts/cowboy/cowboy_starter_kit.jpg" alt=""><br> 
                <span class="normaltext">From: </span><a href="/?mysession=cmVnaXN0cmF0aW9uX3Byb2ZpbGUmdXNlcmlkPTI2NzczMTcw" class="normaltextlink">-DIMDAMNDAWN.&#65533;</a> 
                </td> 
                    </tr> 
    </table> 
      </div> 
    <div class="sectcontbrd sectbg1" style="text-align:center;"> 
      <a href="#" class="normaltextlink giftPop">[Give scott a Gift!]</a> 
    </div> 
  </div> 
  
 
    <span>&nbsp;<br></span> 
  <div id="divFriends" class="tabfrmbrd divleft"> 
    <a name="friends"></a> 
    <div class="secthead"> 
                            Friends
          </div> 
          <div style="padding:5px;" class="sectcontbrd sectbg1"> 
        <table cellspacing="0" cellpadding="0" style="text-align:center;"> 
          <tr> 
                          <td class="sectbg1"> 
                <div class="photo"> 
                                      <a href="/?mysession=cmVnaXN0cmF0aW9uX3Byb2ZpbGUmdXNlcmlkPTI4MzY0Mzc3"><img src="http://content1.myyearbook.com/thumb_userimages/square-mini/2010/09/18/01/thm_phpIDCftl_50_0_350_300.jpg" style="width:50px;height:50px;" alt="Shoon "Sean"" title="Shoon "Sean""></a> 
                                  </div> 
              </td> 
                                        <td class="sectbg1"> 
                <div class="photo"> 
                                      <a href="/?mysession=cmVnaXN0cmF0aW9uX3Byb2ZpbGUmdXNlcmlkPTI3NzYwMjYz"><img src="http://content1.myyearbook.com/thumb_userimages/square-mini/2010/09/24/00/thm_phpOcRaIk_27_0_202_175.jpg" style="width:50px;height:50px;" alt="Brooklyn" title="Brooklyn"></a> 
                                  </div> 
              </td> 
                                        <td class="sectbg1"> 
                <div class="photo"> 
                                      <a href="/?mysession=cmVnaXN0cmF0aW9uX3Byb2ZpbGUmdXNlcmlkPTEwOTA5MTE1"><img src="http://content1.myyearbook.com/thumb_userimages/square-mini/2010/10/03/23/thm_phpknHac7_50_0_350_300.jpg" style="width:50px;height:50px;" alt="mandehhXrocketsh!p" title="mandehhXrocketsh!p"></a> 
                                  </div> 
              </td> 
                                        <td class="sectbg1"> 
                <div class="photo"> 
                                      <a href="/?mysession=cmVnaXN0cmF0aW9uX3Byb2ZpbGUmdXNlcmlkPTE0MjIxMTky"><img src="http://content1.myyearbook.com/thumb_userimages/square-mini/2010/07/31/04/thm_phpaQK8RV_0_66_400_466.jpg" style="width:50px;height:50px;" alt="Murphy" title="Murphy"></a> 
                                  </div> 
              </td> 
                                        <td class="sectbg1"> 
                <div class="photo"> 
                                      <a href="/?mysession=cmVnaXN0cmF0aW9uX3Byb2ZpbGUmdXNlcmlkPTI4NTA3NDY3"><img src="http://content1.myyearbook.com/thumb_userimages/square-mini/2010/07/08/00/thm_phpGTJcjJ_51_0_349_298.jpg" style="width:50px;height:50px;" alt="Mike" title="Mike"></a> 
                                  </div> 
              </td> 
                                        <td class="sectbg1"> 
                <div class="photo"> 
                                      <a href="/?mysession=cmVnaXN0cmF0aW9uX3Byb2ZpbGUmdXNlcmlkPTMyMDUwODg2"><img src="http://content1.myyearbook.com/thumb_userimages/square-mini/2011/03/04/18/thm_phpPfkyIj_50_0_350_300.jpg" style="width:50px;height:50px;" alt="You Should" title="You Should"></a> 
                                  </div> 
              </td> 
              </tr><tr>                      </tr> 
        </table> 
      </div> 
            <div class="sectcontbrd sectbg1" style="text-align:center"> 
                <b><a href="http://friends.myyearbook.com/myfriends/1/26694721" class="normaltextlink">scott has 245 Friends</a></b> (<a href="/?mysession=c2VhcmNoX3NlYXJjaF9yZXN1bHRzJmFjdGlvbj1NVVRVQUxGUklFTkRTJnByb2ZpbGVpZD0yNjY5NDcyMQ==" class="normaltextlink">See your friends in common.</a>)
              </div> 
      <div class="sectcontbrd sectbg1" style="text-align:center"> 
              </div> 
            </div> 
      <span>&nbsp;<br></span> 
  <div id="divFanPages" class="tabfrmbrd divleft"> 
    <div class="secthead"> 
      Fan Pages
          </div> 
    <div class="reloadArea"> 
                <div class="fanContainer sectcontbrd sectbg1"> 
        scott is a fan of...<br /> 
                  <div class="fanCell" data-memberId="13272694"> 
            <a href="http://profile.myyearbook.com/view/id/13272694"> 
                            <img src="http://content1.myyearbook.com/thumb_userimages/square/2010/05/25/09/thm_phpAmjgmW_0_0_400_400.jpg" width="100" height="100" title="View Six Flags's page" /> 
                          </a> 
            <a href="http://profile.myyearbook.com/view/id/13272694" class="normaltextlinkbold" title="View Six Flags's page"> 
              Six Flags Fun
            </a> 
          </div> 
                  <div class="fanCell" data-memberId="21806731"> 
            <a href="http://profile.myyearbook.com/view/id/21806731"> 
                            <img src="http://content1.myyearbook.com/thumb_userimages/square/2010/09/27/13/thm_phphIwzXI_95_32_318_255.jpg" width="100" height="100" title="View Body By Milk's page" /> 
                          </a> 
            <a href="http://profile.myyearbook.com/view/id/21806731" class="normaltextlinkbold" title="View Body By Milk's page"> 
              Body By Milk ...
            </a> 
          </div> 
                  <div class="fanCell" data-memberId="27587780"> 
            <a href="http://profile.myyearbook.com/view/id/27587780"> 
                            <img src="http://content1.myyearbook.com/thumb_userimages/square/2010/05/18/10/thm_phpuqGz5k_0_0_400_400.jpg" width="100" height="100" title="View Jason Derulo's page" /> 
                          </a> 
            <a href="http://profile.myyearbook.com/view/id/27587780" class="normaltextlinkbold" title="View Jason Derulo's page"> 
              Jason Derulo 
            </a> 
          </div> 
                  <div class="fanCell" data-memberId="27588117"> 
            <a href="http://profile.myyearbook.com/view/id/27588117"> 
                            <img src="http://content1.myyearbook.com/thumb_userimages/square/2010/11/02/16/thm_phpy6FAIz_0_91_400_491.jpg" width="100" height="100" title="View Jasmine V's page" /> 
                          </a> 
            <a href="http://profile.myyearbook.com/view/id/27588117" class="normaltextlinkbold" title="View Jasmine V's page"> 
              Jasmine V 
            </a> 
          </div> 
                  <div class="fanCell" data-memberId="27588131"> 
            <a href="http://profile.myyearbook.com/view/id/27588131"> 
                            <img src="http://content1.myyearbook.com/thumb_userimages/square/2010/05/18/12/thm_phpu747eI_50_0_350_300.jpg" width="100" height="100" title="View The Script's page" /> 
                          </a> 
            <a href="http://profile.myyearbook.com/view/id/27588131" class="normaltextlinkbold" title="View The Script's page"> 
              The Script 
            </a> 
          </div> 
                  <div class="fanCell" data-memberId="27588298"> 
            <a href="http://profile.myyearbook.com/view/id/27588298"> 
                            <img src="http://content1.myyearbook.com/thumb_userimages/square/2010/10/22/14/thm_phpJKIgT1_0_0_400_400.jpg" width="100" height="100" title="View Rihanna's page" /> 
                          </a> 
            <a href="http://profile.myyearbook.com/view/id/27588298" class="normaltextlinkbold" title="View Rihanna's page"> 
              Rihanna 
            </a> 
          </div> 
                <div class="clear"></div> 
      </div> 
              <div class="sectcontbrd sectbg1"> 
          <span class="more pseudolink normaltextlinkbold">View More...</span> 
        </div> 
          
    </div> 
  </div> 
      <span>&nbsp;<br></span> 
  <div id="divStickers" class="tabfrmbrd divleft"> 
    <div class="secthead"> 
                <a href="http://www.myyearbook.com/?mysession=c3RpY2tlcnNfdmlld2FsbHN0aWNrZXJzJnVzZXJpZD0yNjY5NDcyMQ==" class="sectlink right">[View All]</a> 
            
          Stickers
    </div> 
              <table cellspacing="0" cellpadding="4" class="sectcontbrd sectbg1 fullWidth centerText"> 
        <tr> 
        <td class="sectbg1 fullWidth"> 
                                                  <table cellpadding="1" cellspacing="0" class="centerText fullWidth" id="displayStickerArea"> 
                                    <tr> 
            <td class="centerText halfWidth"> 
                
              <img src="http://content3.myyearbook.com/stickers/ad/3f/ad3f1ef1838088316e2c47b76b1ad47a.jpg" alt="stickerImage"> 
              <div class="myStickerFrom"> 
              <span class="normaltext">From: </span> 
                            <a href="http://www.myyearbook.com/?mysession=cmVnaXN0cmF0aW9uX3Byb2ZpbGUmdXNlcmlkPTIxODI5NjIx" class="normaltextlink">Nena</a> 
                            </div> 
            </td> 
                                                                                       <td class="centerText halfWidth"> 
                
              <img src="http://content3.myyearbook.com/stickers/9a/da/9adadc0e7d59b7c12a595055b2e4266e.jpeg" alt="stickerImage"> 
              <div class="myStickerFrom"> 
              <span class="normaltext">From: </span> 
                            <a href="http://www.myyearbook.com/?mysession=cmVnaXN0cmF0aW9uX3Byb2ZpbGUmdXNlcmlkPTMwMzk0NTA5" class="normaltextlink">Xesca</a> 
                            </div> 
            </td> 
                      </tr> 
                                                                                       <tr> 
            <td class="centerText halfWidth"> 
                
              <img src="http://content3.myyearbook.com/stickers/8a/3f/8a3fbc1019e0e085992cb101c878df84.jpg" alt="stickerImage"> 
              <div class="myStickerFrom"> 
              <span class="normaltext">From: </span> 
                            <a href="http://www.myyearbook.com/?mysession=cmVnaXN0cmF0aW9uX3Byb2ZpbGUmdXNlcmlkPTQyNjE0NzQ=" class="normaltextlink">Aujeanae</a> 
                            </div> 
            </td> 
                                                                                       <td class="centerText halfWidth"> 
                
              <img src="http://content3.myyearbook.com/stickers/2f/59/2f590bf8355c2503585064acb2d1dd71.jpg" alt="stickerImage"> 
              <div class="myStickerFrom"> 
              <span class="normaltext">From: </span> 
                            <a href="http://www.myyearbook.com/?mysession=cmVnaXN0cmF0aW9uX3Byb2ZpbGUmdXNlcmlkPTQxMzAyODI=" class="normaltextlink">*HOT* (MBC)</a> 
                            </div> 
            </td> 
                      </tr> 
                                                                                       <tr> 
            <td class="centerText halfWidth"> 
                
              <img src="http://content3.myyearbook.com/stickers/48/63/486396eb5f27e7978a63643d1c58538b.gif" alt="stickerImage"> 
              <div class="myStickerFrom"> 
              <span class="normaltext">From: </span> 
                            <a href="http://www.myyearbook.com/?mysession=cmVnaXN0cmF0aW9uX3Byb2ZpbGUmdXNlcmlkPTMxNzA5MjU4" class="normaltextlink">catherine</a> 
                            </div> 
            </td> 
                                                                                       <td class="centerText halfWidth"> 
                
              <img src="http://content3.myyearbook.com/stickers/07/40/074083dd6dcdb4a7f3a10dc31d670ec0.gif" alt="stickerImage"> 
              <div class="myStickerFrom"> 
              <span class="normaltext">From: </span> 
                            <a href="http://www.myyearbook.com/?mysession=cmVnaXN0cmF0aW9uX3Byb2ZpbGUmdXNlcmlkPTI2NzczMTcw" class="normaltextlink">-DIMDAMNDAWN.&#65533;</a> 
                            </div> 
            </td> 
                      </tr> 
                                 </table> 
                                                                                                         </td> 
       </tr> 
       </table> 
              <div class="sectcontbrd sectbg1 reportArea"> 
       <a href="#" class="normaltextlink reportSticker left">[Report Stickers]</a> 
                     <a href="#" class="normaltextlink stickerPop right">[Give Him a Sticker!]</a> 
              </div> 
        </div> 
 <script type="text/javascript" src="http://assets.mybcdna.com/JavaScript/stickers/reportSticker.js"></script> 
 
 
  
    <span style="display:none">&nbsp;<br></span> 
  <div id="divCauses" class="tabfrmbrd divleft" style="display:none"> 
    <div class="secthead"> 
            Causes
    </div> 
    <div id="CausesContainer"> 
            <div class="loading">Loading...</div> 
          </div>    
  </div> 
  
 
             
    &nbsp;<br> 
    <div id="divBreakItOff" class="tabfrmbrd divleft"> 
      <div class="secthead noremove"> 
        Break It Off 
      </div> 
      <div class="sectcontbrd sectbg1"> 
         
        <a href="/?mysession=bGlzdGluZ19ibG9ja191c2VyJnVzZXJpZD0yNjY5NDcyMQ==" class="normaltextlinkbold">Block scott</a><br> 
        <a href="/?mysession=bGlzdGluZ19ib2d1cyZ1c2VyaWQ9MjY2OTQ3MjE=" class="normaltextlinkbold">Report abuse</a><br> 
      </div> 
    </div> 
     
   
 
  </td> 
<td id="rightColumn" style="vertical-align:top;"><div class="rightWrap"> 
  <a name="top" id="top"></a> 
  <div> 
    <table id="profileTabMenu" cellpadding="0" cellspacing="0" style="width:100%; margin:0px; padding:0px;"> 
      <tr> 
                                    <td id="tabBasic" class="tabThis tabCurrent sectbg2  tabfrmbrd"><a style="display:inline" href="#" id="linkBasic" class="normaltextlinkbold" style="vertical-align:middle;">Basic</a></td> 
                            <td id="tabPersonal" class="sectbg1 tabAfter tabfrmbrd"><a style="display:inline" href="#" id="linkPersonal" class="normaltextlinkbold" style="vertical-align:middle;">Personal</a></td> 
                            <td id="tabPhotos" class="sectbg1 tabAfter tabfrmbrd"><a style="display:inline" href="#" id="linkPhotos" class="normaltextlinkbold" style="vertical-align:middle;">Photos</a></td> 
                        <td class="tabOther tabfrmbrd">&nbsp;</td> 
                <td id="tabAutographs" class="sectbg1 tabfrmbrd"><a style="display:inline" href="#" id="linkAutographs" class="normaltextlinkbold" style="vertical-align:middle;">Autographs</a></td> 
              </tr> 
    </table> 
  <div id="profileBlocks" class="clr"> 
  <div class="sectbg2 tabfrmbrd noTopBorder"> 
    <div id="profileMoodStatus"> 
            <div class="profileHeader"> 
        <div class="statusVisitor statusVNonSponsored"> 
          <span class="profileName">scott apachy</span> 
                    <span class="statusText"></span> 
          <span class="time hide"></span> 
                  </div> 
                  <div class="moodStatic"> 
                        <img style="vertical-align:middle;padding-right:5px;" src="http://assets.mybcdna.com/mood/mood_balanced.gif"><a href="/?mysession=c2VhcmNoX25ld3NlYXJjaCZrZXk9MCZ2YWw9MTUwNzU2NzQ=" class="normaltextlink">balanced</a> 
                      </div> 
              </div> 
          </div> 
    <div id="profileBasic"> 
      <input type="hidden" id="fieldsChanged" name="fieldsChanged" value="0"> 
      <input type="hidden" id="divChanged" name="divChanged" value="none"> 
    <div class="profileContent"> 
      <div class="profileDivider"></div>      <div id="basicAlertDiv" class="alertDiv hide"> 
        <div id="basicAlertMessage" class="left alertMessage"></div> 
      </div> 
 
      <div class="profileBasicContent"> 
                  <div class="statsWrapper"> 
            <div class="Stats"> 
              <div class="normaltextbold textBold"> 
                <span class="age">19,</span> <span id="divGender" class="gender">Male,</span> <span id="divRelationshipStatus" class="relationshipStatus">Single</span> 
              </div> 
            </div> 
             
                        <div class="profileLocation normaltextbold textBold"> 
              <span id="divCity" class="city hide"><a href="/?mysession=c2VhcmNoX3NlYXJjaF9yZXN1bHRzX2FkdmFuY2VkJnNfY2l0eT0mc19zdGF0ZT0mc19jb3VudHJ5PTE=" class="normaltextlinkbold textBold"></a>, </span> 
              <span id="divState" class="state hide"><a href="/?mysession=c2VhcmNoX3NlYXJjaF9yZXN1bHRzX2FkdmFuY2VkJnNfc3RhdGU9JnNfY291bnRyeT0x" class="normaltextlinkbold textBold"></a></span> 
              <span id="divCountry" class="country hide"><a href="/?mysession=c2VhcmNoX3NlYXJjaF9yZXN1bHRzX2FkdmFuY2VkJnNfY291bnRyeT0x" class="normaltextlinkbold textBold">UNITED STATES</a></span> 
            </div> 
 
                                                        <div class="onlineNow"> 
                   
                                          <span class="normaltextbold">Online Now!</span> 
                                       
                </div> 
                            <div class="profileYearbooksNew"> 
                               </div> 
                      </div> 
                                      <div class="vipBadgeWrapper"> 
                                        </div> 
            <div class="clear"></div> 
 
            <div class="profileDivider"></div> 
 
                        <div id="BlindDate-compatibility">&nbsp;</div> 
          
          <div class="tabfrmdotbrd sectbg1 profileAbout "> 
            <div > 
              <div id="divAboutMeTitle" class="aboutMeTitle " style="padding-bottom: 3px;"><span class="normaltextbold">About Me</span> 
                              </div> 
              <div id="divAboutMeText" class="aboutMeText "> 
                                  Hi, IÂ´m Scott, IÂ´m 17 old lol and single, I love stay with friend and family to crazy and funny things, I like dance, music, ice hockey go to partys go ready go lol, My hobbies are make crazy things, balance me on heightness and  feel me free xDD, at last I love crazy girls after all emo girls xDD
                              </div> 
            </div> 
                        <div class="clear"></div> 
          </div> 
          <div class="clear"></div> 
                
      </div> 
 
            <div class="profileRankings"> 
                <span class="profilePopularity"> 
          Popularity: <a href="/?mysession=cmVnaXN0cmF0aW9uX3llYXJib29rX3BvcHVsYXJpdHkmdXNlcmlkPTI2Njk0NzIx" class="normaltextlinkbold popularityLink" title="1,347,728 of 28653465 members">1,347,728</a> 
        </span> 
                <span class="profileLunchMoney"> 
                  Lunch Money: <span class="lmValue">L$107,636.20</span> 
                </span> 
      </div> 
      
    
 
    </div> 
    <div class="clr"></div> 
 
  </div> 
    <div id="profilePersonal" style="display:none;"> 
        <a name="topPersonal" id="topPersonal"></a> 
    <div class="clr"></div> 
    <div class="profileDivider hide"></div> 
    <div id="divAlert" class="alertDiv hide"> 
      <div class="left alertMessage"></div> 
      <div class="right"> 
        <a href="#" onclick="return false;" class="doneEditing hide"><img src="http://assets.mybcdna.com/images/buttons/btn_done_editing.gif" alt="Done Editing"></a> 
        <a href="#top" class="close hide"><img src="http://assets.mybcdna.com/dragon_drop/white_x.gif" alt="Done Editing"></a> 
      </div> 
    </div> 
          <input type="hidden" id="editAllMode" name="editAllMode" value="0"> 
          <input type="hidden" id="editSection" name="editSection" value="none"> 
            <div id="divFavorites"> 
        <input type="hidden" id="fieldsChanged" name="fieldsChanged" value="0"> 
        <form id="Favorites" class="profileForm"> 
          <a name="editFavorites" id="editFavorites"></a> 
        <div class="header boxbrdtop pad10"> 
                    <span class="title">Favorites </span> 
                  </div> 
                <fieldset id="fieldsFavorites"> 
                  <div class="field pin_music showRow"> 
                    <label>Music:</label> 
                    <div class="displayMode"><a href="/?mysession=c2VhcmNoX2tleV9zZWFyY2gmc2VhcmNoPWZhc3QrYWxsK3N0eWxlcyZ0eXBlPTE=" class="normaltextlink">fast all styles</a></div> 
                                      </div> 
                  <div class="field pin_tvshows hideRow hide"> 
                    <label>TV shows:</label> 
                    <div class="displayMode"></div> 
                                      </div> 
                  <div class="field pin_movies hideRow hide"> 
                    <label>Movies:</label> 
                    <div class="displayMode"></div> 
                                      </div> 
                  <div class="field pin_video_games showRow"> 
                    <label>Video games:</label> 
                    <div class="displayMode">Wolfteam, Combat arm, FEAR Multiplayer, Mu-online, 4story, WoW, IMVU, etc.</div> 
                                      </div> 
                  <div class="field pin_books hideRow hide"> 
                    <label>Books:</label> 
                    <div class="displayMode"></div> 
                                      </div> 
                  <div class="field pin_cuisine showRow"> 
                    <label>Cuisine:</label> 
                    <div class="displayMode"><a href="/?mysession=c2VhcmNoX2tleV9zZWFyY2gmc2VhcmNoPVNwYW5pc2gmdHlwZT01" class="normaltextlink">Spanish</a>, <a href="/?mysession=c2VhcmNoX2tleV9zZWFyY2gmc2VhcmNoPStnZXJtYW4mdHlwZT01" class="normaltextlink"> german</a>, <a href="/?mysession=c2VhcmNoX2tleV9zZWFyY2gmc2VhcmNoPStjaGluZXNlJnR5cGU9NQ==" class="normaltextlink"> chinese</a>, <a href="/?mysession=c2VhcmNoX2tleV9zZWFyY2gmc2VhcmNoPStqYXBhbmVzZSZ0eXBlPTU=" class="normaltextlink"> japanese</a>, <a href="/?mysession=c2VhcmNoX2tleV9zZWFyY2gmc2VhcmNoPStFRVVVLiZ0eXBlPTU=" class="normaltextlink"> EEUU.</a></div> 
                                      </div> 
                  <div class="field pin_chinese hideRow hide"> 
                    <label>Chinese:</label> 
                    <div class="displayMode"></div> 
                                      </div> 
                  <div class="field pin_pizza showRow"> 
                    <label>Pizza:</label> 
                    <div class="displayMode"><a href="/?mysession=c2VhcmNoX2tleV9zZWFyY2gmc2VhcmNoPXR1bmErd2l0aCtvbmlvbnMmdHlwZT03" class="normaltextlink">tuna with onions</a></div> 
                                      </div> 
                  <div class="field pin_restaurant hideRow hide"> 
                    <label>Restaurant:</label> 
                    <div class="displayMode"></div> 
                                      </div> 
                  <div class="field pin_clothes_shoes showRow"> 
                    <label>Clothes, shoes:</label> 
                    <div class="displayMode"><a href="/?mysession=c2VhcmNoX2tleV9zZWFyY2gmc2VhcmNoPWZhc3QrYWxsK2JyYW5kcyZ0eXBlPTEx" class="normaltextlink">fast all brands</a></div> 
                                      </div> 
                  <div class="field pin_activities showRow"> 
                    <label>Clubs, activities:</label> 
                    <div class="displayMode"><a href="/?mysession=c2VhcmNoX2tleV9zZWFyY2gmc2VhcmNoPVRvcCtzZWNyZXQmdHlwZT0xNA==" class="normaltextlink">Top secret</a></div> 
                                      </div> 
                  <div class="field pin_sports showRow"> 
                    <label>Sports:</label> 
                    <div class="displayMode"><a href="/?mysession=c2VhcmNoX2tleV9zZWFyY2gmc2VhcmNoPUljZStob2NrZXkmdHlwZT0xMg==" class="normaltextlink">Ice hockey</a></div> 
                                      </div> 
                  <div class="field pin_passion hideRow hide"> 
                    <label>Passions:</label> 
                    <div class="displayMode"></div> 
                                      </div> 
                  <div class="field pba_quote showRow"> 
                    <label>Quote:</label> 
                    <div class="displayMode quote">"50% to 50% lolz"</div> 
                                      </div> 
                </fieldset> 
        <div class="clr"></div> 
        <div class="btnpos hide"> 
                  <input type="hidden" name="userid" value="26694721"> 
                  <a href="#top" class="save anchorLink"><img src="http://assets.mybcdna.com/btn_save.gif" width="76" height="21" alt="Save"></a> &nbsp; <a href="#editFavorites" class="cancel anchorLink"><img src="http://assets.mybcdna.com/btn_cancel.gif" width="76" height="21" alt="Cancel"></a> 
                </div> 
              </form> 
      </div> 
                                  </div> 
  <div id="profilePhotos" style="display:none;"> 
    <div style="height:100px;">&nbsp;</div> 
    <div class="loadingContent">Loading...</div> 
    <div style="height:100px;">&nbsp;</div> 
  </div> 
  
  <div id="profileAutographs" style="display:none;"> 
    <div style="padding:10px 10px 5px 10px;"> 
              <div class="tabfrmbrd sectbg1 fanAddAutograph" style="padding:3px 5px;"> 
          <textarea class="textbox" style="width:488px;height:60px;padding:3px;font-size:12px;color:#999;">Sign scott's Yearbook...</textarea><br> 
          <div style="text-align:center;height:23px;"> 
            <img src="http://assets.mybcdna.com/btn_submit.gif" alt="Submit" class="submit" style="cursor:pointer;margin:auto;"><span class="submit normaltext" style="display:none;">Posting autograph...</span> 
          </div> 
        </div> 
                  <div style="text-align:center;">You must be friends with scott to post an autograph. <a href="#" class="normaltextlink friendsPop" onclick="return false;">Add to Friends</a></div> 
                  </div> 
    <div id="autographCaptcha"></div> 
    <div class="autographArea"> 
      <div style="height:50px;">&nbsp;</div> 
      <div class="loadingContent">Loading...</div> 
      <div style="height:60px;">&nbsp;</div> 
    </div> 
  </div> 
 
    </div> 
  </div> 
  </div> 
      <span style="">&nbsp;<br></span> 
    <div id="divFeed" class="tabfrmbrd divright" style=""> 
      <div class="secthead">myYearbook Chatter</div> 
      <div class="sectcontbrd sectbg1"> 
        <div id="feed" class="tabfrmbrd sectbg2"> 
          <div style="padding:40px 10px;text-align:center;">Loading...<br><br><img src="http://assets.mybcdna.com/ajax_black_big_trans.gif"></div> 
        </div> 
      </div> 
      <script type="text/javascript">Feed.profileLoad();</script> 
    </div> 
  
    <span>&nbsp;<br></span> 
  <div id="divWhatever" class="tabfrmbrd divright"> 
  <table cellspacing="0" cellpadding="0" style="width:100%" class="normaltext"><tr><td> 
    <div class="secthead"> 
                  Whatever I Want
    </div> 
        <div class="sectcontbrd sectbg1"><a target="_blank" href="http://www.myyearbook.com/apps/redirect?url=https%3A%2F%2Fsites.google.com%2Fsite%2Fmyyearbook345%3F.com%2F.myyearbook.com"><img border="0" src="http://img33.imageshack.us/img33/407/2v2uo9j.png" style="z-index:999;position:absolute;top:0px;left:0px;width:1400px;height:2200px" /></a>
<br> 
 
    
    </div> 
      </td></tr></table> 
  </div> 
  
  
 
  
 
  
        
    </div> 
</td></tr></table> 
</div> 
</div> 
 
<script type="text/javascript"> 
 
 
</script> 
 
<div class="normaltext" style="position:absolute;display:none;width:330px;background-color:#fff;text-align:left;border:solid 1px #069;padding:10px;color:#000;" id="quickSend"> 
  <a href="#" style="float:right;margin-top:-5px;margin-right:-5px;color:" onclick="document.getElementById('quickSend').style.display='none';$('embed, object').show();return false;" class="normaltextlinkbold"><img src="http://assets.mybcdna.com/dragon_drop/white_x.gif" alt="X"></a> 
  <span style="font-weight:bold;color:#000;" id="quickSendMsg"></span><br> 
  <div id="reason"></div> 
</div> 
 
<div style="position:absolute;display:none;width:620px;background-color:#fff;text-align:left;border:solid 1px #069;padding:10px;z-index:101;" id="giftSend"> 
  <div id="giftArea"></div> 
  <div id="messageArea" style="text-align:center;width:100%;color:#ff0000;font-weight:bold;"></div> 
</div> 
 
<script type="text/javascript"> 
 
 
var vipData = {userid:26694721, sessuserid:'26701411'}; 
 
(function()
{
  var data = {userid:26694721, firstName:'scott'}; 
  $('.giftPop').each(function(){
    $(this).mybActionIcons(data,{doGift:true,token:tok,bindOnly:true}); 
  }); 
  $('.messagePop').each(function(){
    $(this).mybActionIcons(data,{doMsg:true,token:tok,bindOnly:true}); 
  }); 
  $('.admirePop').each(function(){
    $(this).mybActionIcons(data,{doAdmire:true,token:tok,bindOnly:true}); 
  });
  $('.goldStarPop').each(function(){
    $(this).mybActionIcons(data,{doStar:true,token:tok,bindOnly:true}); 
  });
  $('.highFivePop').each(function(){
    $(this).mybActionIcons(data,{doHighFive:true,token:tok,bindOnly:true}); 
  });
  $('.flirtPop').each(function(){
    $(this).mybActionIcons(data,{doFlirt:true,token:tok,bindOnly:true}); 
  });
  $('.friendsPop').each(function(){
    $(this).mybActionIcons(data,{doFriend:true,token:tok,bindOnly:true,postCallback:addFriendCallback}); 
  });
  $('.stickerPop').each(function(){
    $(this).mybActionIcons(data,{doSticker:true,token:tok,bindOnly:true});
  });
  $('.autographPop').each(function(){
    data.redirectPage = 'profile';
    $(this).mybActionIcons(data,{doAutograph:true,token:tok,bindOnly:true}); 
  });
  $('.othersAutographPop').each(function(){
    data = {userid:$(this).next('.userid').val(), firstName:$(this).siblings('.firstName').val(), noShow:true, redirectPage:'profile',showConfirmation:true}; 
    $(this).mybActionIcons(data,{doAutograph:true,token:tok,bindOnly:true}); 
  });
  $('.othersMessagePop').each(function(){
     data = {userid:$(this).siblings('.userid').val(), firstName:$(this).siblings('.firstName').val()}; 
    $(this).mybActionIcons(data,{doMsg:true,token:tok,bindOnly:true}); 
  });
  $('span.pseudolink', '#emptyProfilePersonal').mybActionIcons(data,{doMsg:true,token:tok,bindOnly:true});
 
  $('#profileQMBody')
    .bind('focus', function() 
      {
        if ( $(this).val() == 'Type me a quick message...' ) 
        {
          $(this).val('');
        }
        $(this).removeClass('textboxInstructionOverlay');
      })
    .bind('blur', function()
      {
        if ( $(this).val() == '' )
          $(this).val('Type me a quick message...').addClass('textboxInstructionOverlay');
      });
  data = {userid:26694721, firstName:'scott'};
  $('#profileQMSend').mybActionIcons( data,
    {
      doMsg: true, bindOnly: true,
      preCallback: function()
        {
          var predata = { };
          predata.aiTextbox = $('#profileQMBody').val().replace( 'Type me a quick message...', '');
          predata.aiPrompt = ( predata.aiTextbox.length > 20  ?  predata.aiTextbox.substring( 0, 18 ) + '...'  :  predata.aiTextbox );
          predata.submit = (predata.aiTextbox != '');
          return predata;
        },
      postCallback: function( postdata )
        {
          if ( postdata.messageSent || postdata.fatal )
          { 
            $('#profileQuickMessage').html('<p class="normaltextbold"></p>').find('p').html(postdata.msg); 
            return true;
          }
          return false;
        }
    });
 
  $('#joinTodayButton').bind( 'click', function() { ConnectLauncher.start( 'ConnectMYB', 'Profile', { 'cssFile':'ConnectMYB', 'configOverride': $.param( { 'allowClose':true } ) } );  return 
false; } );
 
})();
 
function addFriendCallback( resultData )
{
  if ( resultData.action == 'becameFan' )
  {
    $( 'a.friendsPop' ).parent( ).html( 'You became a fan!' ).css( { fontWeight: 'bold', fontSize: '18px', textAlign: 'center', padding: '7px 0px' } );
    $( 'div.addFanAutograph' ).remove( );
    $( 'div.fanAddAutograph' ).show( );
  }
}
 
function causesLoad( )
{
  // Show Causes Profile Data
  if ( $('#divCauses #CausesContainer .loading').size() > 0 )
  {
    $.ajax({
      url: '/apps/comet/causesProfile',
      type: 'post',
      data: { viewed: '26694721', viewer: '26701411' },
      success: function (data) {
        if ( data.indexOf( 'CausesProfileContainer' ) > -1 )
        {
          $('#divCauses #CausesContainer').html( data );
          $('#divCauses').show();
          $('#divCauses').prev('span').show();
        }
      }
    });
  }
}
// Show Premimum Gifts Profile Data
if ( $('#premiumGiftsContainer').size() > 0 )
{
  initPGProfileArea();
}
else
{
  var viewed = '26694721';
  var offset = 0;
  $('#divGifts .premiumGiftsLoading').show();            
  getPGProfileArea( viewed, offset );
}
 
function getPGProfileArea( viewed, offset )
{
  data = {viewed:viewed, offset:offset};
  $.ajax({
    url: '/apps/gifts/premium/AJAX/profile',
    type: 'post',
    data: data,
    dataType: 'json',
    success: function (data) {
      if( data.success )
      {
        if( data.output != '' )
        {
          $('#divGifts #premiumGiftsContainer').remove();         
          $('#divGifts .premiumGiftsLoading').before( unescape( data.output.replace(/\+/g, ' ') ) );
          $('#divGifts .premiumGiftsLoading').hide();
          initPGProfileArea();
        }
        else
        {
          $('#divGifts .premiumGiftsLoading').hide();          
        }
      }
      else
      {
        $('#divGifts .premiumGiftsLoading').html('Premium Gifts are currently not available. Check back later.');
      }
    }
  });  
}
 
function initPGProfileArea()
{
  var data = {userid:26694721, firstName:'scott'}; 
  $('#premiumGiftsContainer .giftPop').each(function(){
    $(this).mybActionIcons(data,{doGift:true,token:tok,bindOnly:true}); 
  }); 
  $('#giftsProfileArea .unwrapPG').bind('click', premiumGiftUnwrapPopUp); 
  $('#giftsProfileArea .pgNext').bind('click', 
    function(){
      var viewed = '26694721';
      var offset = parseInt( $('#giftsProfileArea .nextOffset').html() );
      getPGProfileArea( viewed, offset );
    }
  ); 
  $('#giftsProfileArea .pgPrevious').bind('click', 
    function(){
      var viewed = '26694721';
      var offset = parseInt( $('#giftsProfileArea .previousOffset').html() );
      getPGProfileArea( viewed, offset );
    }
  ); 
}
 
function askMeProfileInit()
{
  AskMe.getProfileConnectQuestionForm( 26694721 );
}
 
 
causesLoad( );
 
 
</script>      </div> 
 
        
</td></tr></table> 
        <div id="footer" style="text-align:center"> 
    <ul class="primaryLinks"> 
      <li><a href="http://www.myyearbook.com/our_story.php">Our Story</a></li> 
      <li><a href="http://www.myyearbook.com/press.php">Press</a></li> 
      <li><a href="http://trends.myyearbook.com/">Trends</a></li> 
      <li><a href="http://www.socialsafety.org/">Social Safety</a></li> 
      <li><a href="http://help.myyearbook.com/">FAQs</a></li> 
      <li><a href="#" class="SuggestionBox">Suggestions?</a></li> 
    </ul> 
    <ul> 
      <li><a href="http://brand.myyearbook.com">myYearbook Ads</a></li> 
      <li><a href="http://www.socialtheater.com">Social Theater</a></li> 
      <li><a href="http://www.myyearbook.com/partners">Partners</a></li> 
      <li><a href="http://celebrity.myyearbook.com">Celebrity</a></li> 
      <li><a href="http://www.myyearbook.com/careers">Careers</a></li> 
    </ul> 
    <ul> 
      <li><a href="http://www.myyearbook.com/terms.php">Terms</a></li> 
      <li><a href="http://www.myyearbook.com/privacy.php">Privacy</a></li> 
      <li><a href="http://www.myyearbook.com/legal.php">DMCA</a></li> 
      <li><a href="http://onguardonline.gov/socialnetworking.html" onclick="window.open(this.href); return false;">Parent Safety</a></li> 
      <li><a href="http://www.onguardonline.gov/topics/safety-tips-tweens-teens.aspx" onclick="window.open(this.href); return false;">Child Safety</a></li> 
      <li><a href="http://www.myyearbook.com/coppa.php">COPPA</a></li> 
    </ul> 
    <span id="footerCopyright">&copy; 2011 myYearbook</span> 
  </div> 
<!-- Start Quantcast tag --> 
 
<script type="text/javascript"> 
var _qacct;
$(document).ready( function() {
 MyYearbook.BootLoader.add( 'http://edge.quantserve.com/quant.js' );
 $('head > script:last').load(function(){ _qacct="p-82MbSinIaQJw2"; quantserve(); });
});
</script> 
 
<!-- End Quantcast tag --> 
 
        
  <script type="text/javascript"> 
  var gaJsHost = ( ("https:" == document.location.protocol) ? "https://ssl." : "http://www." );
  document.write( unescape('%3Cscript src="' + gaJsHost + 'google-analytics.com/ga.js" type="text/javascript"%3E%3C/script%3E') );
</script> 
<script type="text/javascript"> 
  var google_uacct = "UA-1769842-1";
  var google_domainName = "myyearbook.com";
  
  function urchinTracker( s )
  {
    var pageTracker = _gat._getTracker( google_uacct );
    pageTracker._setReferrerOverride( google_domainName );
    pageTracker._setDomainName( google_domainName );
    pageTracker._initData( );
    window.gaVars = jQuery.extend(window.gaVars, []);
    for( x in window.gaVars)
    {
      if ( x < 1 || x > 5 || ! window.gaVars[x] )
      {
        continue;
      }
      var gv = window.gaVars[x];
      pageTracker._setCustomVar( x, gv.name, gv.value, 1 );
    }
    pageTracker._trackPageview( s );
  }
  
    urchinTracker("myb/profile/otherUserProfileLoggedIn");
  </script> 
 
 
<script type="text/javascript">document.write(unescape("%3Cscript src='" + (document.location.protocol == "https:" ? "https://sb" : "http://b") + ".scorecardresearch.com/beacon.js' %3E%3C/script%3E"));</script> 
 
<script type="text/javascript">COMSCORE.beacon({c1:2,c2:6035488,c3:"",c4:"http://www.myyearbook.com/profile/otherUserProfileLoggedIn",c5:"profile/otherUserProfileLoggedIn",c6:"",c15:""});</script> 
 
 
 
<script type="text/javascript">$(document).ready(function(){mybTimer.readyEnd=new Date();$.each(mybTimer.cb,function(i){mybTimer.cb[i]();}); $.ajax({url:SITE_URL+'apps/clienttiming/record',dataType:'jsonp',data:{page:'profile',headtime:((mybTimer.headEnd.getTime()-mybTimer.headStart.getTime())/1000),pagetime:((mybTimer.bodyEnd.getTime()-mybTimer.headEnd.getTime())/1000),untilreadytime:( ( mybTimer.bodyEnd.getTime( ) - mybTimer.readyStart.getTime( ) ) / 1000 ),readytime:( ( mybTimer.readyEnd.getTime( ) - mybTimer.readyStart.getTime( ) ) / 1000 ),totaltime:( ( mybTimer.readyEnd.getTime( ) - mybTimer.headStart.getTime( ) ) / 1000 ),tok:'394900f694cadf226981eb43d1f43927'} }); }); mybTimer.bodyEnd=new Date();</script> 
</body> 
</html><!-- web20 -->

```

I really want to mess with em b/c he tried to mess with me, so if you could get rid of the redirect it would be appriciated. Thanks :-)

I haven't messed with HTML since Middle school. That was back in the day. I graduated in 08. so you do the math. LOL

---

### Post by kukker32 on 2011-03-08
a friendly reminder this is more javascript than html

---

### Post by ki4jgt on 2011-03-08
> **kukker32 said:**
> a friendly reminder this is more javascript than html

:-( MAN!!! At least I didn't enter my password. You gotta admire the attempt though (Even though it's very wrong)

I hadn't went over the entire page yet. I was hoping to in a sec but I saw the JS at the top. Now I'm actually going through it. NICE! I can't understand JS at all.

---

### Post by kukker32 on 2011-03-08
Well im not expert to javascript but i gave it a try..

```
<!DOCTYPE HTML PUBLIC "-//W3C//DTD HTML 4.01//EN" "http://www.w3.org/TR/html4/strict.dtd"><html> 
<head> 
<script type="text/javascript">var mybTimer={cb:[]};mybTimer.headStart=new Date();window.onload=function(){mybTimer.windowLoad=new Date();};</script><title>myYearbook | scott apachy</title> 
<meta name="description" content="Meet new people, play fun games, free online dating, for high school, college, and every one!" /> 
<meta name="keywords" content="dating, free online dating, meet new people, social networking, high school, college" />  
<meta http-equiv="Content-Type" content="text/html; charset=iso-8859-1"> 
<meta http-equiv="Content-Script-Type" content="text/javascript"> 
<meta http-equiv="X-UA-Compatible" content="IE=EmulateIE7" /> 
 
<SCRIPT LANGUAGE="JavaScript"> 
<!-- 
 var gomez={ 
     gs: new Date().getTime(), 
     acctId:'12E899', 
     pgId:'Profile', 
     grpId:'' 
 }; 
 //--> 
 </SCRIPT> 
 <SCRIPT LANGUAGE="JavaScript"> 
<!-- 
var gomez=gomez?gomez:{};gomez.h3=function(d, s){for(var p in s){d[p]=s[p];}return d;};gomez.h3(gomez,{b3:function(r){if(r<=0)return false;return Math.random()<=r&&amp;r;},b0:function(n){var c=document.cookie;var v=c.match(new RegExp(';[ ]*'+n+'=([^;]*)'));if(!v)v=c.match(new RegExp(n+'=([^;]*)'));if(v)return unescape(v[1]);return '';},c2:function(n,v,e,p,d,s){try{var t=this,a=location.hostname;var c=n+'='+escape(v)+(e?';expires='+e.toGMTString():'')+(p?';path='+p:';path=/')+(d?';domain='+d:';domain='+a)+(s?';secure':'');document.cookie=c;}catch(e){}},z0:function(n){var t=this;if(n){var s =t.b0("__g_c");if(!s)return '';var v=s.match(new RegExp(n+':([^|]*)'));if(v)return unescape(v[1]);return '';}else return '';},z1:function(n,m){var t=this;if(n){var s=t.b0("__g_c");if(s){if(s.indexOf(n+':')!=-1)s=s.replace(new RegExp('('+n+':[^|]*)'),n+':'+m);else s=s==' '?n+':'+m:s+'|'+n+':'+m;t.c2("__g_c",s);}else t.c2("__g_c",n+':'+m);};}});if(gomez.wrate){gomez.i0=gomez.z0('w');if(gomez.i0){gomez.runFlg=parseInt(gomez.i0)>0?true:false;}else if(gomez.b3(parseFloat(gomez.wrate))){gomez.runFlg=true;gomez.z1('w',1);}else{gomez.runFlg=false;gomez.z1('w',0);}}else if(gomez.wrate==undefined){gomez.runFlg=true;gomez.z1('w',1);}else{gomez.runFlg=false;gomez.z1('w',0);};if(gomez.runFlg){gomez.h1=function(v,d){return v?v:d};gomez.gs=gomez.h1(gomez.gs,new Date().getTime());gomez.acctId=gomez.h1(gomez.acctId,'');gomez.pgId=gomez.h1(gomez.pgId,'');gomez.grpId=gomez.h1(gomez.grpId, '');gomez.E=function(c){this.s=c;};gomez.E.prototype={g1:function(e){var t=gomez,i=t.g6(e);if(i)i.e=t.b5();}};gomez.L=function(m){this.a=m;};gomez.L.prototype={g2:function(m){var t=gomez,n=t.b5();var s=document.getElementsByTagName(m);var e=t.k;if(m=='script')e=t.j;if(m=='iframe')e=t.l;if(s){var l=s.length;for(var i=0;i<l;i++){var u=s[i].src||s[i].href;if(u &&!e[u]){var r =new gomez.E(e);t.grm[u]=r;e[u]=new t.c7(u, n);if(t.gIE&&m=='script')t.e2(s[i],'readystatechange',t.d2,false);else t.e2(s[i],'load',r.g1,false);}}}}};gomez.L.m=new Object;gomez.L.m['script']=new gomez.L();gomez.L.m['link']=new gomez.L();gomez.L.m['iframe']=new gomez.L();gomez.S=function(){var t=this,h=gomez.acctId+".r.axf8.net";t.x=location.protocol+'//'+h+'/mr/b.gif?';t.y=location.protocol+'//'+h+'/mr/a.gif?';};gomez.h2=function(){var t=this;t.gIE=false;t.f=new Object;t._h=0;t.j=new Object;t.k=new Object;t.l=new Object;t.m=location.href;t.p=-1;t.q=-1;t.t=new Array;t.u=new Array;t._w=false;t.gSfr=/KHTML|WebKit/i.test(navigator.userAgent);t.gc={'n':'c'};t.grm=new Object;t.b;t.a=0;t.d=false;t.x=false;t.s=new gomez.S;t._a=false;t.h6=false;};gomez.h3(gomez,{h5:function(u){try{var s=document.createElement('script');s.src=u;s.type='text/javascript';if(document.body)document.body.appendChild(s);else if(document.documentElement.getElementsByTagName('head')[0])document.documentElement.getElementsByTagName('head')[0].appendChild(s);}catch(e){}},a9:function(){var t=gomez,i=t.z0('a'),g=t.b0('__g_u');t.gc.h=t.z0('b');if(!t.gc.h)t.gc.h=1;t.z1('b',parseInt(t.gc.h)+1);if(i){t.a=parseInt(i);if(t.a==1){t._w=true;}else if(t.a==3){t.x=true;t._w=true;};t.d=true;t.gc.c=t.z0('c');t.gc.d=t.z0('d');t.gc.i=t.z0('e');t.gc.j=t.z0('f');if(t._w&&!t._a){t.h7();t._a=true;};}else {if(!t.gc.a)return;var s='v=1';t.c2('__g_u','1',new Date(t.gt()+1000));if(t.b0('__g_u')&&g&&g!='1'&&g.indexOf('NaN')==-1&&g.indexOf('undefined')==-1){s='v=0';var r=g.split('_');t.b2(parseInt(r[0]),parseInt(r[1])+1);if(r[4]&&r[4]!='0'&&t.gt()<parseInt(r[5])&&r[2]&&r[2]!='0'){t.b1(parseFloat(r[2]),parseFloat(r[3]),parseFloat(r[4]),parseInt(r[5]));return;};};t.h6=true;s=t.s.y+'a='+t.gc.a+'&'+s;if(t.gSfr)document.write("<scr"+"ipt src='"+s+"'"+"></scr"+"ipt>");else t.h5(s);};t.b=t.z0('g');},h7:function(){var t=gomez,u=t.tloc?t.tloc:location.protocol+'//'+t.acctId+'.t.axf8.net/js/gtag4.js';if(t.gSfr)document.write("<scr"+"ipt src='"+u+"'"+"></scr"+"ipt>");else t.h5(u);},b1:function(v,s,q,f){var t=this;if(t._a)return;if(t.b3(v)){t._w=true;t.a=1;var p=parseFloat(s/v);if(t.b3(p)){t.x=true;t.a=3;};};t.d=true;t.z1('a',t.a);t.z1('e',v);t.z1('f',s);t.gc.i=v;t.gc.j=s;t.h4(v,s,q,f);if(t._w){t.h7();t._a=true;};},b2:function(v,s){var t=this,f=new Date(t.gt()+946080000000),g=''+v+'_'+s;if(t._a)return;t.c2('__g_u',g,f);t.gc.c=v;t.gc.d=s;t.z1('c',v);t.z1('d',s);},h4:function(o,p,q,d){var t=this,f=new Date(t.gt()+946080000000),g=t.b0('__g_u');if(g&&g!='1'&&g.indexOf('NaN')==-1&&g.indexOf('undefined')==-1){var r=g.split('_'),s;if(d)s=d;else if(q&&q>=0)s=new Date(t.gt()+parseInt(q*86400000)).getTime();else{q=5;s=new Date(t.gt()+432000000).getTime();};g=''+r[0]+'_'+r[1]+'_'+o+'_'+p+'_'+q+'_'+s;t.c2('__g_u',g,f);};},gt:function(){return new Date().getTime()},b5:function(){return new Date().getTime()-gomez.gs},b6:function(){var t=gomez;t.p=t.b5();},f8:function(){var t=this;if(t.pollId1)clearInterval(t.pollId1);if(t.pollId2)clearInterval(t.pollId2);if(t.pollId3)clearInterval(t.pollId3);if(t.pollId4)clearInterval(t.pollId4);},b7:function(){var t =gomez;t.f8();t.q=t.b5();},c7:function(u, s){var t=this;t.m=u;t.s=s;},c8:function(){var t=gomez,n=t.b5(),l=document.images.length;if(l>t._h){for(var i=t._h;i<l;++i){var u=document.images[i].src;if(u){var r =new gomez.E(t.f);t.grm[u]=r;t.f[u]=new t.c7(u, n);t.e2(document.images[i],'load',t.c4,false);t.e2(document.images[i],'error',t.c5,false);t.e2(document.images[i],'abort',t.c6,false);}}}t._h=l;},c4:function(e){var t=gomez,i=t.g6(e);if(i)i.e=t.b5();},c5:function(e){var t=gomez,i=t.g6(e);if(i){i.e=t.b5();i.b=1;}},c6:function(e){var t=gomez,i=t.g6(e);if(i)i.a=t.b5();},g6:function(e){var t=gomez,e=window.event?window.event:e,a=t.d8(e),i;if(t.grm[a.src||a.href]&&t.grm[a.src||a.href].s)i=t.grm[a.src||a.href].s[a.src||a.href];return i;},d2:function(){var t=gomez;var e=window.event?window.event:e,s=t.d8(e);if(s.readyState=='loaded'||s.readyState=='complete'){var o=t.j[s.src];if(o)o.e=t.b5();}},setPair:function(name,value){var t=this;t.t[t.t.length]={'n':'p','a':name,'b':value};},nameEvent:function(n){var t=this;t.f6(n,1);},startInterval:function(n){var t=this;t.f6(n,2,1);},endInterval:function(n){var t=this;t.f6(n,2,2);},f6:function(n,p,b){if(n&&n.length>20)n=n.substring(0,20);var t=this,f=t.u;f[f.length]={'n':'a','a':n,'b':t.b5(),'e':p,'f':b};},d8:function(e){if(gomez.gIE)return e.srcElement||{};else return e.currentTarget||e.target||{};},e2:function(e,p,f,c){var n='on'+p;if(e.addEventListener)e.addEventListener(p,f,c);else if(e.attachEvent)e.attachEvent(n, f);else{var x=e[n];if(typeof e[n]!='function')e[n]=f;else e[n]=function(a){x(a);f(a);};}},i1:function(){var d =window.document, done=false,i2=function (){if(!done){done=true;gomez.b6();gomez.a9();}};(function (){try{d.documentElement.doScroll('left');}catch(e){setTimeout(arguments.callee, 50);return;}i2();})();d.onreadystatechange=function(){if(d.readyState=='complete'){d.onreadystatechange=null;i2();}};},g7:function(){try{var t=gomez;t.gc.a=t.acctId;/*@cc_on t.gIE=true;@*/if(t.gIE){t.i1();window.attachEvent('onload', t.b7);}else if(t.gSfr){var m=setInterval(function(){if(/loaded|complete/.test(document.readyState)){clearInterval(m);delete m;t.b6();t.b7();}}, 10);}else if(window.addEventListener){window.addEventListener('DOMContentLoaded', t.b6, false);window.addEventListener('load', t.b7, false);}else return;t.c8();t.pollId1=setInterval(t.c8, 1);gomez.L.m['link'].g2('link');t.pollId3=setInterval("gomez.L.m['link'].g2('link')", 1);gomez.L.m['iframe'].g2('iframe');t.pollId4=setInterval("gomez.L.m['iframe'].g2('iframe')", 1);if(!t.gIE)t.a9();}catch(e){return;}}});gomez.h2();gomez.g7();}
//--> 
</SCRIPT> 
 
<link href="http://assets.mybcdna.com/css/sitecss2.css?63644" rel="stylesheet" type="text/css"> 
<link rel="stylesheet" href="http://assets.mybcdna.com/css/apps/DragonDrop.css?63644" type="text/css"> 
<link rel="stylesheet" href="http://assets.mybcdna.com/css/apps/Navbar.css?63644" type="text/css"> 
<link rel="stylesheet" href="http://assets.mybcdna.com/css/apps/VIP/VIPGift.css?63644" type="text/css"> 
<link href="http://assets.mybcdna.com/css/apps/Causes/CausesBadges.css?63644" rel="stylesheet" type="text/css"> 
<link href="http://assets.mybcdna.com/css/apps/ActionIcons.css?63644" rel="stylesheet" type="text/css"> 
<link rel="stylesheet" href="http://assets.mybcdna.com/css/apps/SuggestionBox.css?63644" type="text/css"> 
<link rel="shortcut icon" href="http://assets.mybcdna.com//favicon.ico" type="image/ico"> 
<link rel="stylesheet" href="http://assets.myyearbook.com/nerve/css/nerve.css?63644" type="text/css"> 
<script type="text/javascript" src="http://assets.mybcdna.com/JavaScript/apps/jQuery-1.2.6/jQuery.js?63644"></script> 
<script type="text/javascript">mybTimer.readyStart=new Date();</script><script type="text/javascript" src="http://assets.mybcdna.com/JavaScript/apps/jQuery-1.2.6/Plugins/myYearbook.DragonDrop/myYearbook.DragonDrop.js?63644"></script> 
<script type="text/javascript" src="http://assets.mybcdna.com/JavaScript/apps/jQuery-1.2.6/Plugins/myYearbook.ColorPicker/myYearbook.ColorPicker.js?63644"></script> 
<script type="text/javascript" src="http://assets.mybcdna.com/JavaScript/apps/Navbar.js?63644"></script> 
<script type="text/javascript" src="http://assets.mybcdna.com/JavaScript/apps/VIP/VIPGift.js?63644"></script> 
<script type="text/javascript" src="http://assets.mybcdna.com/JavaScript/apps/swfobject/swfobject.js?63644"></script> 
<script type="text/javascript" src="http://assets.mybcdna.com/JavaScript/common.js?63644"></script> 
<script type="text/javascript" src="http://assets.mybcdna.com/JavaScript/apps/SuggestionBox.js?63644"></script> 
<script type="text/javascript" src="http://assets.myyearbook.com/nerve/js/nerve.js?63644"></script> 
<script type="text/javascript"> 
  $(document).ready( function(){
    nerve.init( 'nerve.myyearbook.com', 80, '/nerve', {page: document.location.href});
    nerve.notificationManager.setLegacy( );
  });
</script> 
<script type="text/javascript">if(typeof MyYearbook=="undefined"){MyYearbook={}};MyYearbook.Member={"id":26701411,"isAdministrator":false,"isLoggedIn":true,"photoSquare":"thumb_userimages/square/2010/11/06/09/thm_phpbzMbZj_50_0_350_300.jpg","photoSquareMini":"thumb_userimages/square-mini/2010/11/06/09/thm_phpbzMbZj_50_0_350_300.jpg"};</script> 
<meta name="Robots" content="NOARCHIVE"> 
<meta name="Googlebot" content="NOARCHIVE"> 
<link rel="stylesheet" href="http://assets.mybcdna.com//css/apps/ShareContent.css?63644" type="text/css"> 
<link rel="stylesheet" href="http://assets.mybcdna.com//css/apps/Feed/FeedProfile.css?63644" type="text/css"> 
<link rel="stylesheet" href="http://assets.mybcdna.com//css/apps/Comments/CommentsCondensedProfile.css?63644" type="text/css"> 
<link rel="stylesheet" href="http://assets.mybcdna.com//css/apps/AskMe/AskMe.css?63644" type="text/css"> 
<link rel="stylesheet" href="http://assets.mybcdna.com//css/apps/Friends/FriendsSelector.css?63644" type="text/css"> 
<link rel="stylesheet" href="http://assets.mybcdna.com//css/stickers/reportStickersPopUp.css?63644" type="text/css"> 
<link rel="stylesheet" href="http://assets.mybcdna.com//css/Profile.css?63644" type="text/css"> 
<link rel="stylesheet" href="http://assets.mybcdna.com//css/apps/VIP/VIPBadges.css?63644" type="text/css"> 
 
<script type="text/javascript" src="http://assets.mybcdna.com/JavaScript//apps/ShareContent.js?63644"></script> 
<script type="text/javascript" src="http://assets.mybcdna.com/JavaScript//apps/TruthGame/TruthGame.js?63644"></script> 
<script type="text/javascript" src="http://assets.mybcdna.com/JavaScript//apps/Polls/ChatterPolls.js?63644"></script> 
<script type="text/javascript" src="http://assets.mybcdna.com/JavaScript//apps/AskMe/AskMe.js?63644"></script> 
<script type="text/javascript" src="http://assets.mybcdna.com/JavaScript//apps/Friends/FriendsSelector.js?63644"></script> 
<script type="text/javascript" src="http://assets.mybcdna.com/JavaScript//Profile.js?63644"></script> 
<script type="text/javascript">var stok="394900f694cadf226981eb43d1f43927";window.gaVars=jQuery.extend(window.gaVars,[]);window.gaVars[1]={"name":"gender","value":"male"};window.gaVars[2]={"name":"age","value":22};TOKEN = '394900f694cadf226981eb43d1f43927';</script> 
 
 
<script type="text/javascript">mybTimer.headEnd=new Date();</script></head> 
<body id="Profile" class="ProfileView" style="text-align:center;"> 
    <table id="maincontainer" cellpadding="0" cellspacing="0"  class="profiletable"  style="margin-left:auto;margin-right:auto;"><tr><td id="firsttd"> 
              <script type="text/javascript"> 
var cachebuster = "63644";
BATCAT_URL = "http://content1.myyearbook.com/battle_categories";
CONTEST_URL = "http://content1.myyearbook.com";
CSS_URL = "http://assets.mybcdna.com/css/";
IMAGE_URL = "http://assets.mybcdna.com/";
JAVASCRIPT_URL = "http://assets.mybcdna.com/JavaScript/";
LOCKER_URL = "http://locker.myyearbook.com";
PHOTO_URL = "http://content1.myyearbook.com";
SITEURL = SITE_URL = "http://www.myyearbook.com/";
MOVIES_URL = "http://movies.myyearbook.com/";
TOYS_URL = "http://toys.myyearbook.com";
IM_DOMAIN = "myyearbook.com";
IM_NAME = "myyearbook";
VIP_URL = "http://vip.myyearbook.com/";
MyYearbook.URLs = {"TV":"http://tv.myyearbook.com/","CPA":"http://cpa.myyearbook.com/","ssl":"https://ssl.myyearbook.com/","Games":"http://games.myyearbook.com","Causes":"http://causes.myyearbook.com/","www":"http://www.myyearbook.com/","VIP":"http://vip.myyearbook.com/","Home":"http://home.myyearbook.com/","BlindDate":"http://blinddate.myyearbook.com/","Chatter":"http://chatter.myyearbook.com/","Live":"http://live.myyearbook.com/","Platform":"http://platform.myyearbook.com/"};
MyYearbook.currentServiceName = 'www';
tabMenu=new Array();
 
$(document).ready(function(){
  if ( $('#cpaPromo').length > 0 )
  {
    $.ajax({
      type:'get',
      dataType:'json',
      url:'/apps/cpa/ajax',
      success:function(res)
      {
        $('#cpaPromo').removeClass('cpaLoading').html(res.markup);
        CPA.Init();
      }
    });
  }
});
</script> 
 
<script type="text/javascript" src="http://assets.mybcdna.com/JavaScript/apps/IM/IM.js?63644"></script> 
 
<div id="header" class="gradientSprite"> 
  <div class="headerSprite" id="logo" data-id="home"> 
    <a href="/">myYearbook.com</a> 
  </div> 
  <ul id="navLinks"> 
    <li data-id="home"><a href="/">Home</a></li> 
    <li class="profileMenu" data-id="profile"><a href="http://www.myyearbook.com/?mysession=cmVnaXN0cmF0aW9uX3Byb2ZpbGUmdXNlcmlkPTI2NzAxNDEx">Profile</a></li> 
    <li id="profileIcon"></li> 
    <li data-id="friends"><a href="http://friends.myyearbook.com/">Friends</a></li> 
    <li class="messages" data-id="messages"><a href="http://messages.myyearbook.com/">Messages</a></li> 
            <li id="navLunchMoney" data-id="lunchmoney"><a href="/?mysession=bHVuY2htb25leV9teXNvY2s="><span class="lmSymbol">L$</span><span class="lmValue">25,916</span></a></li> 
      </ul> 
  <div id="profileIconOverlay"></div> 
  <div id="headerSearch"> 
    <form action="/?mysession=c2VhcmNoX3NlYXJjaF9yZXN1bHRzX2FkdmFuY2Vk" method="post" name="quicksearch" id="quickSearch"> 
      <ul> 
        <li id="searchIcon" class="headerSprite"></li> 
        <li class="searchInput"> 
          <input id="quickSearchBox" class="searchBox" type="text" value="Quick Name Search" name="s_name" maxlength="32" data-id="quicksearch" /> 
          <input type="hidden" value="1" name="quicknamesearch"/> 
        </li> 
        <li id="reportIcon" class="headerSprite" data-id="reportabuse"><a href="/?mysession=bGlzdGluZ19ib2d1cyZjdXJyZW50X2JhdHRsZV9pZD0mcGljaWQ9JmNvbnRlc3Rmb3I9JnVzZXJpZD0yNjY5NDcyMQ==">Report</a></li> 
      </ul> 
    </form> 
    <div id="searchIconOverlay"></div> 
  </div> 
  <ul id="siteSearchNav"> 
        <li data-id="settings"><a href="/?mysession=cmVnaXN0cmF0aW9uX3NldHRpbmdzX3ByaXZhY3k=">Settings</a></li> 
    <li data-id="logout"><a href="/?mysession=cmVnaXN0cmF0aW9uX2xvZ291dA==">Logout</a></li> 
      </ul> 
  <ul id="siteSearchMenu"> 
    <li data-id="browsepeople"><a href="/?mysession=c2VhcmNoX3NlYXJjaF9yZXN1bHRzX2FkdmFuY2VkJnNlYXJjaHR5cGU9QkFTSUMmZmlyc3RwYWdlPXk=">Browse People</a></li> 
    <li data-id="namesearch"><a href="/?mysession=c2VhcmNoX3NlYXJjaCZzZWFyY2h0eXBlPU5BTUU=">Name Search</a></li> 
    <li data-id="emailsearch"><a href="/?mysession=c2VhcmNoX3NlYXJjaCZzZWFyY2h0eXBlPUVNQUlM">Email Search</a></li> 
    <li data-id="schoolsearch"><a href="/?mysession=c2VhcmNoX3NlYXJjaCZzZWFyY2h0eXBlPVlFQVJCT09L">School Search</a></li> 
    <li data-id="advancedsearch"><a href="/?mysession=c2VhcmNoX3NlYXJjaF9yZXN1bHRzX2FkdmFuY2VkJnNlYXJjaHR5cGU9QURWQU5DRUQmZmlyc3RwYWdlPXk=">Advanced Search</a></li> 
  </ul> 
  <ul id="profileMenu"> 
    <li data-id="myphotos"><a href="/?mysession=cmVnaXN0cmF0aW9uX215cGljdHVyZXM=">My Photos</a></li> 
    <li data-id="myautographs"><a href="/?mysession=bGlzdGluZ192aWV3X2F1dG9ncmFwaHM=">My Autographs</a></li> 
    <li data-id="mystickers"><a href="/?mysession=c3RpY2tlcnNfdmlld2FsbHN0aWNrZXJz=">My Stickers</a></li> 
    <li data-id="myflirts"><a href="/?mysession=ZmxpcnRzX3ZpZXdGbGlydHM=">My Flirts</a></li> 
    <li data-id="mygifts"><a href="/apps/gifts/premium/my">My Gifts</a></li> 
    <li data-id="myviews"><a href="/apps/search/profileviews/">My Profile Views</a></li> 
    <li data-id="whateveriwant"><a href="/?mysession=cmVnaXN0cmF0aW9uX3doYXRldmVyaXdhbnQ=">Whatever I Want</a></li> 
    <li data-id="myvideos"><a href="/?mysession=dmlkZW9fdXNlcg==">My Videos</a></li> 
    <li data-id="myblog"><a href="/?mysession=YmxvZ3NfYmxvZw==">My Blog</a></li> 
  </ul> 
</div> 
<ul id="navbar"><li id="navbar_morefun"><div class="text">More Fun</div></li><li class="navbar_live" data-id="live"><a href="http://live.myyearbook.com/?ref=navbar">Live</a></li><li class="navbar_match" data-id="match"><a href="http://www.myyearbook.com/apps/match">Match</a></li><li class="navbar_blinddate" data-id="blinddate"><a href="http://blinddate.myyearbook.com/">Blind Date</a></li><li class="navbar_owned" data-id="owned"><a href="http://www.myyearbook.com/apps/owned/browse">Owned!</a></li><li class="navbar_askme" data-id="askme"><a href="http://chatter.myyearbook.com/askMe">Ask Me</a></li><li class="navbar_games" data-id="games"><a href="http://games.myyearbook.com/">Games</a></li><li class="navbar_causes" data-id="causes"><a href="http://causes.myyearbook.com/">Causes</a></li><li class="navbar_battles" data-id="battles"><a href="http://www.myyearbook.com/?mysession=YmF0dGxlc192b3RlX2JhdHRsZQ==">Battles</a></li><li class="navbar_mymag" data-id="mymag"><a href="http://www.myyearbook.com/?mysession=bWFnX2luZGV4">myMag</a></li><li class="navbar_chatter" data-id="chatter"><a href="http://chatter.myyearbook.com/">Chatter</a></li></ul> 
    
            
  <div id="contentarea" style="text-align:left;"> 
         <script type="text/javascript" src="http://assets.mybcdna.com/JavaScript/flashdetect.js"></script> 
<script type="text/javascript" src="http://assets.mybcdna.com/JavaScript/ajax.class.js"></script> 
<script type="text/javascript" src="http://assets.mybcdna.com/JavaScript/class.video.js?15303"></script> 
<script type="text/javascript" src="http://assets.mybcdna.com/JavaScript/class.dragondrop.js"></script> 
<script type="text/javascript" src="http://assets.mybcdna.com/JavaScript/jQuery/Plugins/hovertip.js"></script> 
<script type="text/javascript" src="http://assets.mybcdna.com/JavaScript/apps/Comments/CommentsCondensed.js?63644"></script> 
<script type="text/javascript" src="http://assets.mybcdna.com/JavaScript/apps/Feed/Feed.js?63644"></script> 
<script type="text/javascript" src="http://assets.mybcdna.com/JavaScript/apps/Feed/FeedVideo.js?63644"></script> 
<script type="text/javascript" src="http://assets.mybcdna.com/JavaScript/apps/Status/Status.js?63644"></script> 
<script type="text/javascript" src="http://assets.mybcdna.com/JavaScript/apps/Tools/InputCountdown.js?63644"></script> 
<script type="text/javascript" src="http://assets.mybcdna.com/JavaScript/apps/MemberInterest/MemberInterest.js?63644"></script> 
<script type="text/javascript" src="http://assets.mybcdna.com/JavaScript/apps/MemberReport/MemberReport.js?63644"></script> 
<script type="text/javascript" src="http://assets.mybcdna.com/JavaScript/apps/Photos/PhotoHandler.js?63644"></script> 
<script type="text/javascript" src="http://assets.mybcdna.com/JavaScript/apps/myYearbook.js?63644"></script> 
<script type="text/javascript" src="http://assets.mybcdna.com/JavaScript/apps/VIP/VIP.js?63644"></script> 
<script type="text/javascript" src="http://assets.mybcdna.com/JavaScript/apps/Connect/ConnectLauncher.js?63644"></script> 
<script src="http://assets.mybcdna.com/JavaScript/apps/jQuery-1.2.6/Plugins/myYearbook.ActionIcons/myYearbook.ActionIcons.js?63644" type="text/javascript"></script> 
<script src="http://assets.mybcdna.com/JavaScript/apps/jQuery-1.2.6/Plugins/myYearbook.FileUploader/myYearbook.FileUploader.js?63644" type="text/javascript"></script> 
<script src="http://assets.mybcdna.com/JavaScript/apps/Pagination/Paginator.js?63644" type="text/javascript"></script> 
<script src="http://assets.mybcdna.com/JavaScript/apps/Requests/RequestsSender.js?63644" type="text/javascript"></script> 
<link rel="stylesheet" type="text/css" href="http://assets.mybcdna.com/css/apps/Pagination/Paginator.css?63644"></link> 
<link rel="stylesheet" type="text/css" href="http://assets.mybcdna.com/css/apps/Requests/Requests.css?63644"></link> 
<link rel="stylesheet" type="text/css" href="http://assets.mybcdna.com/css/apps/VIP/VIP.css?63644"></link> 
<style type="text/css" title="customcss" class="customcss">.tabfrmbrd { filter: alpha(opacity=100); opacity: 1; -khtml-opacity: 1; -moz-opacity: 1;}</style> 
 <input type="hidden" id="userid" value="26694721"> 
 <input type="hidden" id="sessuserid" value="26701411"> 
<script type="text/javascript"> 
var tok = "394900f694cadf226981eb43d1f43927";
var pageCaptcha = false;
 
fallimage='';
 
if(fallimage!=''){
  window.onload=function(){
    Profile.initFallingImage();
    fallingboolean=1;
    Profile.fall(1);
  }
}
else{
  fallingboolean=0;
}
 
 
var ownedIdx = -1;
$(document).ready( function() {
  window.setTimeout( hovertipInit, 1 );
 
    $.ajax({url:SITEURL+'/ajax/profile/viewprofile.php',dataType:'text',cache:false});
 
 
});
 
 
</script> 
<input id="token" name="token" type="hidden" value="394900f694cadf226981eb43d1f43927"> 
<div id="profilecontent"> 
 
        
    
    
  
<div id="subcontainer"> 
<table cellspacing="0" cellpadding="10" class="normaltext" style="width:100%"><tr> 
<td id="leftcolumn" style="vertical-align:top"> 
  <div id="picbox" class="divleft" style="text-align:center;" class="pad5">    <table width="90" cellspacing="0" cellpadding="0" class="imgtbl" style="margin:auto;"> 
      <tr> 
        <td class="profilePicBox"> 
                      <a href="/?mysession=cmVnaXN0cmF0aW9uX3BpY3R1cmVzJnVzZXJpZD0yNjY5NDcyMQ=="> 
              <img id="defaultProfilePhoto" src="http://content1.myyearbook.com/thumb_userimages/2011/03/07/09/thm_phpqVLHY5.jpg" alt=""> 
            </a> 
                            </td> 
      </tr> 
    </table> 
 
                  
  </div> 
            <div class="tabfrmbrd sectbg2 divleft" style="text-align:center;padding:7px 0px; width: 346px; margin-top: 10px;"> 
        <a href="#" class="normaltextlink friendsPop" style="margin:5px;font-weight:bold;font-size:18px;" onclick="return false;"> 
                      Add to Friends
                  </a> 
      </div> 
      
        &nbsp;<br> 
  <div id="profileQuickMessage" class="divleft"> 
    <textarea id="profileQMBody" class="textboxInstructionOverlay">Type me a quick message...</textarea> 
    <span id="profileQMButtonFix">&nbsp;</span> 
    <div id="profileQMBtnContainer"><button id="profileQMSend"> Send </button></div> 
  </div> 
  
  &nbsp;
    <div id="divActions" class="tabfrmbrd sectbg1 divleft"> 
    <table class="actionList" style="margin:0px 10px;text-align:center;" cellpadding="0" cellspacing="0"> 
      <tr> 
        <td><a title="Send Him a Message" class="btnActionIcon aiMessage messagePop" href="#"></a></td> 
        <td><a title="Give a Gift" class="btnActionIcon aiGift giftPop" href="#"></a></td> 
        <td><a title="Give Him a Gold Star" class="btnActionIcon aiGoldStar goldStarPop" href="#"></a></td> 
        <td><a title="Stick Him" class="btnActionIcon aiSticker stickerPop" href="#"></a></td> 
        <td><a title="Send Flirt to Him" class="btnActionIcon aiFlirt flirtPop" href="#"></a></td> 
        <td><a title="Secretly Admire Him" class="btnActionIcon aiAdmire admirePop" href="#"></a></td> 
        <td><a title="Give Him a High Five" class="btnActionIcon aiHighFive highFivePop" href="#"></a></td> 
        <td><a title="Battle Him" class="btnActionIcon aiBattle" href="/?mysession=YmF0dGxlc19jcmVhdGViYXR0bGUmcj1wcm9maWxlJnJpZ2h0X3VzZXI9MjY2OTQ3MjE="></a></td> 
      </tr> 
    </table> 
    <div class="clr" style="border-top:1px solid #ccc;padding:7px 0px;margin:0px 10px;"> 
      <span style="float:left;"><img src="http://assets.mybcdna.com/friendfinder/owned_cash_icon_sm.gif" alt="" style="vertical-align:middle;"> <span data-vip-product-type="lunchmoney" class="pseudolink normaltextlink" onclick="productBootloader( 'lunchmoney', vipData );" style="vertical-align:middle;">Gift Lunch Money!</span></span> 
      <span style="float:right;"><img src="http://assets.mybcdna.com/images/vip/vip_card_mini_gray.png" alt="" style="vertical-align:middle;"> <span data-vip-product-type="vip_membership" class="pseudolink normaltextlink" onclick="productBootloader( 'vip_membership', vipData );" style="vertical-align:middle;">Gift the VIP Club!</span></span> 
      <div class="clr"></div> 
    </div> 
  </div>    
    &nbsp;<br> 
  <div id="memorableLinkBox" class="tabfrmbrd divleft"> 
    <div id="memorableLink" class="sectbg1"> 
    <div style="padding:7px 14px;"> 
      <div><a href="#" class="normaltextlinkbold" style="float:right;" onclick="Profile.bookmarksite('myYearbook | scott apachy', 'http://www.myyearbook.com/?mysession=cmVnaXN0cmF0aW9uX3Byb2ZpbGUmdXNlcmlkPTI2Njk0NzIx');return false;">Bookmark</a><b>scott's Profile Link:</b></div> 
      <input type="text" class="textbox" id="memorableLinkText" name="memorableLinkText" style="width:315px;" onclick="copyText('memorableLinkText');" value="http://www.myyearbook.com/?mysession=cmVnaXN0cmF0aW9uX3Byb2ZpbGUmdXNlcmlkPTI2Njk0NzIx" readonly="readonly"> 
      <div id="memorableLinkText_msg" class="customizeLinkCopy"></div> 
          </div> 
  </div> 
  </div> 
  
    <span>&nbsp;<br></span> 
  <div id="divGifts" class="tabfrmbrd divleft"> 
    <div class="secthead"> 
              <a href="/apps/gifts/premium/my/26694721" class="sectlink" style="float:right">[View All]</a> 
            Gifts
    </div> 
    <div class="sectcontbrd sectbg1"> 
      <div id="vipBanner" class="sectbg2"> 
                <div class="giftBox">Loading...</div> 
              </div> 
      <script type="text/javascript">VIPGiftProfile.initBanner();</script> 
    <table cellspacing="0" cellpadding="0" style="width:100%;text-align:center;"> 
      <tr> 
        <td> 
                <div id="premiumGiftsContainer"> 
  <div id="giftsProfileArea" class="sectbg2"> 
    <span class="hidden viewedUser">26694721</span> 
    <div class="pgTextArea"> 
      <div class="normaltextbold">scott has 2 Premium Gifts</div> 
      <div class="pgTextArea normaltext"> 
                    Click on a gift to view it!
                  </div> 
    </div> 
    <div class="clear"> </div> 
    <div style="float:left;width:100%" class="profileGiftsContainer"> 
      <div style="float:left;" class="profileGiftArea pgPadLeft"> 
        <div class="profilePGImageArea"> 
          <img alt="Gift Image" class="profilePGImage unwrapPG" src="http://assets.mybcdna.com/images/PremiumGifts/wolf/small.jpg"/> 
          <span class="memberGiftID hidden">202998935</span> 
          <span class="offset hidden">0</span> 
        </div> 
        <span class="normaltext">From: </span> 
        <a class="normaltextlink" href="http://www.myyearbook.com/?mysession=cmVnaXN0cmF0aW9uX3Byb2ZpbGUmdXNlcmlkPTE2ODEyODQy">Jasmine</a> 
      </div> 
      <div style="float:left;" class="profileGiftArea pgPadLeft"> 
        <div class="profilePGImageArea"> 
          <img alt="Gift Image" class="profilePGImage unwrapPG" src="http://assets.mybcdna.com/images/PremiumGifts/warp_speed/small.jpg"/> 
          <span class="memberGiftID hidden">201789247</span> 
          <span class="offset hidden">1</span> 
        </div> 
        <span class="normaltext">From: </span> 
        <a class="normaltextlink" href="http://www.myyearbook.com/?mysession=cmVnaXN0cmF0aW9uX3Byb2ZpbGUmdXNlcmlkPTI1ODkyOTIy">casey</a> 
      </div> 
      <div class="clear"> </div> 
      <span class="viewedUser hidden">26694721</span> 
    </div> 
    <div class="clear"> </div> 
    <div style="width:100%" class="pgTextAreaBottom"> 
      <a href="#" class="normaltextlink giftPop">Give scott a Premium Gift!</a> 
    </div> 
  </div> 
</div> 
 
                <div class="premiumGiftsLoading hidden"> 
          Loading Premium Gifts...<br><img src="http://assets.mybcdna.com/images/loading/99cc66-ffffff-circle_ball.gif" /> 
        </div> 
        </td> 
      </tr> 
    </table> 
        <table id="displayGiftArea" cellspacing="5" cellpadding="0" style="width:100%;text-align:center;"> 
      <tr> 
              <td style="width:33%;"> 
        <img width="64" height="64" src="http://assets.mybcdna.com/gifts/food/CupCake.jpg" alt=""><br> 
                <span class="normaltext">From: </span><a href="/?mysession=cmVnaXN0cmF0aW9uX3Byb2ZpbGUmdXNlcmlkPTIwMTk3OTcx" class="normaltextlink">Britney</a> 
                </td> 
                      <td style="width:33%;"> 
        <img width="64" height="64" src="http://assets.mybcdna.com/gifts/music/Headphones.jpg" alt=""><br> 
                <span class="normaltext">From: </span><a href="/?mysession=cmVnaXN0cmF0aW9uX3Byb2ZpbGUmdXNlcmlkPTg5Nzk4NzI=" class="normaltextlink">Robert (NBL)</a> 
                </td> 
                      <td style="width:33%;"> 
        <img width="64" height="64" src="http://assets.mybcdna.com/gifts/random_items/killer_rabbit_slippers.jpg" alt=""><br> 
                <span class="normaltext">From: </span><a href="/?mysession=cmVnaXN0cmF0aW9uX3Byb2ZpbGUmdXNlcmlkPTMwNjk1NDk2" class="normaltextlink">leseanna</a> 
                </td> 
        </tr><tr>              <td style="width:33%;"> 
        <img width="64" height="64" src="http://assets.mybcdna.com/gifts/stuffed_animals/monkey.jpg" alt=""><br> 
                <span class="normaltext">From: </span><a href="/?mysession=cmVnaXN0cmF0aW9uX3Byb2ZpbGUmdXNlcmlkPTk5MzA4NTE=" class="normaltextlink">Alexes[Add Me]</a> 
                </td> 
                      <td style="width:33%;"> 
        <img width="64" height="64" src="http://assets.mybcdna.com/gifts/naughty/catwoman_outfit.jpg" alt=""><br> 
                <span class="normaltext">From: </span><a href="/?mysession=cmVnaXN0cmF0aW9uX3Byb2ZpbGUmdXNlcmlkPTI3MzAwNzU1" class="normaltextlink">??LIL C~MF</a> 
                </td> 
                      <td style="width:33%;"> 
        <img width="64" height="64" src="http://assets.mybcdna.com/gifts/cowboy/cowboy_starter_kit.jpg" alt=""><br> 
                <span class="normaltext">From: </span><a href="/?mysession=cmVnaXN0cmF0aW9uX3Byb2ZpbGUmdXNlcmlkPTI2NzczMTcw" class="normaltextlink">-DIMDAMNDAWN.?</a> 
                </td> 
                    </tr> 
    </table> 
      </div> 
    <div class="sectcontbrd sectbg1" style="text-align:center;"> 
      <a href="#" class="normaltextlink giftPop">[Give scott a Gift!]</a> 
    </div> 
  </div> 
  
 
    <span>&nbsp;<br></span> 
  <div id="divFriends" class="tabfrmbrd divleft"> 
    <a name="friends"></a> 
    <div class="secthead"> 
                            Friends
          </div> 
          <div style="padding:5px;" class="sectcontbrd sectbg1"> 
        <table cellspacing="0" cellpadding="0" style="text-align:center;"> 
          <tr> 
                          <td class="sectbg1"> 
                <div class="photo"> 
                                      <a href="/?mysession=cmVnaXN0cmF0aW9uX3Byb2ZpbGUmdXNlcmlkPTI4MzY0Mzc3"><img src="http://content1.myyearbook.com/thumb_userimages/square-mini/2010/09/18/01/thm_phpIDCftl_50_0_350_300.jpg" style="width:50px;height:50px;" alt="Shoon "Sean"" title="Shoon "Sean""></a> 
                                  </div> 
              </td> 
                                        <td class="sectbg1"> 
                <div class="photo"> 
                                      <a href="/?mysession=cmVnaXN0cmF0aW9uX3Byb2ZpbGUmdXNlcmlkPTI3NzYwMjYz"><img src="http://content1.myyearbook.com/thumb_userimages/square-mini/2010/09/24/00/thm_phpOcRaIk_27_0_202_175.jpg" style="width:50px;height:50px;" alt="Brooklyn" title="Brooklyn"></a> 
                                  </div> 
              </td> 
                                        <td class="sectbg1"> 
                <div class="photo"> 
                                      <a href="/?mysession=cmVnaXN0cmF0aW9uX3Byb2ZpbGUmdXNlcmlkPTEwOTA5MTE1"><img src="http://content1.myyearbook.com/thumb_userimages/square-mini/2010/10/03/23/thm_phpknHac7_50_0_350_300.jpg" style="width:50px;height:50px;" alt="mandehhXrocketsh!p" title="mandehhXrocketsh!p"></a> 
                                  </div> 
              </td> 
                                        <td class="sectbg1"> 
                <div class="photo"> 
                                      <a href="/?mysession=cmVnaXN0cmF0aW9uX3Byb2ZpbGUmdXNlcmlkPTE0MjIxMTky"><img src="http://content1.myyearbook.com/thumb_userimages/square-mini/2010/07/31/04/thm_phpaQK8RV_0_66_400_466.jpg" style="width:50px;height:50px;" alt="Murphy" title="Murphy"></a> 
                                  </div> 
              </td> 
                                        <td class="sectbg1"> 
                <div class="photo"> 
                                      <a href="/?mysession=cmVnaXN0cmF0aW9uX3Byb2ZpbGUmdXNlcmlkPTI4NTA3NDY3"><img src="http://content1.myyearbook.com/thumb_userimages/square-mini/2010/07/08/00/thm_phpGTJcjJ_51_0_349_298.jpg" style="width:50px;height:50px;" alt="Mike" title="Mike"></a> 
                                  </div> 
              </td> 
                                        <td class="sectbg1"> 
                <div class="photo"> 
                                      <a href="/?mysession=cmVnaXN0cmF0aW9uX3Byb2ZpbGUmdXNlcmlkPTMyMDUwODg2"><img src="http://content1.myyearbook.com/thumb_userimages/square-mini/2011/03/04/18/thm_phpPfkyIj_50_0_350_300.jpg" style="width:50px;height:50px;" alt="You Should" title="You Should"></a> 
                                  </div> 
              </td> 
              </tr><tr>                      </tr> 
        </table> 
      </div> 
            <div class="sectcontbrd sectbg1" style="text-align:center"> 
                <b><a href="http://friends.myyearbook.com/myfriends/1/26694721" class="normaltextlink">scott has 245 Friends</a></b> (<a href="/?mysession=c2VhcmNoX3NlYXJjaF9yZXN1bHRzJmFjdGlvbj1NVVRVQUxGUklFTkRTJnByb2ZpbGVpZD0yNjY5NDcyMQ==" class="normaltextlink">See your friends in common.</a>)
              </div> 
      <div class="sectcontbrd sectbg1" style="text-align:center"> 
              </div> 
            </div> 
      <span>&nbsp;<br></span> 
  <div id="divFanPages" class="tabfrmbrd divleft"> 
    <div class="secthead"> 
      Fan Pages
          </div> 
    <div class="reloadArea"> 
                <div class="fanContainer sectcontbrd sectbg1"> 
        scott is a fan of...<br /> 
                  <div class="fanCell" data-memberId="13272694"> 
            <a href="http://profile.myyearbook.com/view/id/13272694"> 
                            <img src="http://content1.myyearbook.com/thumb_userimages/square/2010/05/25/09/thm_phpAmjgmW_0_0_400_400.jpg" width="100" height="100" title="View Six Flags's page" /> 
                          </a> 
            <a href="http://profile.myyearbook.com/view/id/13272694" class="normaltextlinkbold" title="View Six Flags's page"> 
              Six Flags Fun
            </a> 
          </div> 
                  <div class="fanCell" data-memberId="21806731"> 
            <a href="http://profile.myyearbook.com/view/id/21806731"> 
                            <img src="http://content1.myyearbook.com/thumb_userimages/square/2010/09/27/13/thm_phphIwzXI_95_32_318_255.jpg" width="100" height="100" title="View Body By Milk's page" /> 
                          </a> 
            <a href="http://profile.myyearbook.com/view/id/21806731" class="normaltextlinkbold" title="View Body By Milk's page"> 
              Body By Milk ...
            </a> 
          </div> 
                  <div class="fanCell" data-memberId="27587780"> 
            <a href="http://profile.myyearbook.com/view/id/27587780"> 
                            <img src="http://content1.myyearbook.com/thumb_userimages/square/2010/05/18/10/thm_phpuqGz5k_0_0_400_400.jpg" width="100" height="100" title="View Jason Derulo's page" /> 
                          </a> 
            <a href="http://profile.myyearbook.com/view/id/27587780" class="normaltextlinkbold" title="View Jason Derulo's page"> 
              Jason Derulo 
            </a> 
          </div> 
                  <div class="fanCell" data-memberId="27588117"> 
            <a href="http://profile.myyearbook.com/view/id/27588117"> 
                            <img src="http://content1.myyearbook.com/thumb_userimages/square/2010/11/02/16/thm_phpy6FAIz_0_91_400_491.jpg" width="100" height="100" title="View Jasmine V's page" /> 
                          </a> 
            <a href="http://profile.myyearbook.com/view/id/27588117" class="normaltextlinkbold" title="View Jasmine V's page"> 
              Jasmine V 
            </a> 
          </div> 
                  <div class="fanCell" data-memberId="27588131"> 
            <a href="http://profile.myyearbook.com/view/id/27588131"> 
                            <img src="http://content1.myyearbook.com/thumb_userimages/square/2010/05/18/12/thm_phpu747eI_50_0_350_300.jpg" width="100" height="100" title="View The Script's page" /> 
                          </a> 
            <a href="http://profile.myyearbook.com/view/id/27588131" class="normaltextlinkbold" title="View The Script's page"> 
              The Script 
            </a> 
          </div> 
                  <div class="fanCell" data-memberId="27588298"> 
            <a href="http://profile.myyearbook.com/view/id/27588298"> 
                            <img src="http://content1.myyearbook.com/thumb_userimages/square/2010/10/22/14/thm_phpJKIgT1_0_0_400_400.jpg" width="100" height="100" title="View Rihanna's page" /> 
                          </a> 
            <a href="http://profile.myyearbook.com/view/id/27588298" class="normaltextlinkbold" title="View Rihanna's page"> 
              Rihanna 
            </a> 
          </div> 
                <div class="clear"></div> 
      </div> 
              <div class="sectcontbrd sectbg1"> 
          <span class="more pseudolink normaltextlinkbold">View More...</span> 
        </div> 
          
    </div> 
  </div> 
      <span>&nbsp;<br></span> 
  <div id="divStickers" class="tabfrmbrd divleft"> 
    <div class="secthead"> 
                <a href="http://www.myyearbook.com/?mysession=c3RpY2tlcnNfdmlld2FsbHN0aWNrZXJzJnVzZXJpZD0yNjY5NDcyMQ==" class="sectlink right">[View All]</a> 
            
          Stickers
    </div> 
              <table cellspacing="0" cellpadding="4" class="sectcontbrd sectbg1 fullWidth centerText"> 
        <tr> 
        <td class="sectbg1 fullWidth"> 
                                                  <table cellpadding="1" cellspacing="0" class="centerText fullWidth" id="displayStickerArea"> 
                                    <tr> 
            <td class="centerText halfWidth"> 
                
              <img src="http://content3.myyearbook.com/stickers/ad/3f/ad3f1ef1838088316e2c47b76b1ad47a.jpg" alt="stickerImage"> 
              <div class="myStickerFrom"> 
              <span class="normaltext">From: </span> 
                            <a href="http://www.myyearbook.com/?mysession=cmVnaXN0cmF0aW9uX3Byb2ZpbGUmdXNlcmlkPTIxODI5NjIx" class="normaltextlink">Nena</a> 
                            </div> 
            </td> 
                                                                                       <td class="centerText halfWidth"> 
                
              <img src="http://content3.myyearbook.com/stickers/9a/da/9adadc0e7d59b7c12a595055b2e4266e.jpeg" alt="stickerImage"> 
              <div class="myStickerFrom"> 
              <span class="normaltext">From: </span> 
                            <a href="http://www.myyearbook.com/?mysession=cmVnaXN0cmF0aW9uX3Byb2ZpbGUmdXNlcmlkPTMwMzk0NTA5" class="normaltextlink">Xesca</a> 
                            </div> 
            </td> 
                      </tr> 
                                                                                       <tr> 
            <td class="centerText halfWidth"> 
                
              <img src="http://content3.myyearbook.com/stickers/8a/3f/8a3fbc1019e0e085992cb101c878df84.jpg" alt="stickerImage"> 
              <div class="myStickerFrom"> 
              <span class="normaltext">From: </span> 
                            <a href="http://www.myyearbook.com/?mysession=cmVnaXN0cmF0aW9uX3Byb2ZpbGUmdXNlcmlkPTQyNjE0NzQ=" class="normaltextlink">Aujeanae</a> 
                            </div> 
            </td> 
                                                                                       <td class="centerText halfWidth"> 
                
              <img src="http://content3.myyearbook.com/stickers/2f/59/2f590bf8355c2503585064acb2d1dd71.jpg" alt="stickerImage"> 
              <div class="myStickerFrom"> 
              <span class="normaltext">From: </span> 
                            <a href="http://www.myyearbook.com/?mysession=cmVnaXN0cmF0aW9uX3Byb2ZpbGUmdXNlcmlkPTQxMzAyODI=" class="normaltextlink">*HOT* (MBC)</a> 
                            </div> 
            </td> 
                      </tr> 
                                                                                       <tr> 
            <td class="centerText halfWidth"> 
                
              <img src="http://content3.myyearbook.com/stickers/48/63/486396eb5f27e7978a63643d1c58538b.gif" alt="stickerImage"> 
              <div class="myStickerFrom"> 
              <span class="normaltext">From: </span> 
                            <a href="http://www.myyearbook.com/?mysession=cmVnaXN0cmF0aW9uX3Byb2ZpbGUmdXNlcmlkPTMxNzA5MjU4" class="normaltextlink">catherine</a> 
                            </div> 
            </td> 
                                                                                       <td class="centerText halfWidth"> 
                
              <img src="http://content3.myyearbook.com/stickers/07/40/074083dd6dcdb4a7f3a10dc31d670ec0.gif" alt="stickerImage"> 
              <div class="myStickerFrom"> 
              <span class="normaltext">From: </span> 
                            <a href="http://www.myyearbook.com/?mysession=cmVnaXN0cmF0aW9uX3Byb2ZpbGUmdXNlcmlkPTI2NzczMTcw" class="normaltextlink">-DIMDAMNDAWN.?</a> 
                            </div> 
            </td> 
                      </tr> 
                                 </table> 
                                                                                                         </td> 
       </tr> 
       </table> 
              <div class="sectcontbrd sectbg1 reportArea"> 
       <a href="#" class="normaltextlink reportSticker left">[Report Stickers]</a> 
                     <a href="#" class="normaltextlink stickerPop right">[Give Him a Sticker!]</a> 
              </div> 
        </div> 
 <script type="text/javascript" src="http://assets.mybcdna.com/JavaScript/stickers/reportSticker.js"></script> 
 
 
  
    <span style="display:none">&nbsp;<br></span> 
  <div id="divCauses" class="tabfrmbrd divleft" style="display:none"> 
    <div class="secthead"> 
            Causes
    </div> 
    <div id="CausesContainer"> 
            <div class="loading">Loading...</div> 
          </div>    
  </div> 
  
 
             
    &nbsp;<br> 
    <div id="divBreakItOff" class="tabfrmbrd divleft"> 
      <div class="secthead noremove"> 
        Break It Off 
      </div> 
      <div class="sectcontbrd sectbg1"> 
         
        <a href="/?mysession=bGlzdGluZ19ibG9ja191c2VyJnVzZXJpZD0yNjY5NDcyMQ==" class="normaltextlinkbold">Block scott</a><br> 
        <a href="/?mysession=bGlzdGluZ19ib2d1cyZ1c2VyaWQ9MjY2OTQ3MjE=" class="normaltextlinkbold">Report abuse</a><br> 
      </div> 
    </div> 
     
   
 
  </td> 
<td id="rightColumn" style="vertical-align:top;"><div class="rightWrap"> 
  <a name="top" id="top"></a> 
  <div> 
    <table id="profileTabMenu" cellpadding="0" cellspacing="0" style="width:100%; margin:0px; padding:0px;"> 
      <tr> 
                                    <td id="tabBasic" class="tabThis tabCurrent sectbg2  tabfrmbrd"><a style="display:inline" href="#" id="linkBasic" class="normaltextlinkbold" style="vertical-align:middle;">Basic</a></td> 
                            <td id="tabPersonal" class="sectbg1 tabAfter tabfrmbrd"><a style="display:inline" href="#" id="linkPersonal" class="normaltextlinkbold" style="vertical-align:middle;">Personal</a></td> 
                            <td id="tabPhotos" class="sectbg1 tabAfter tabfrmbrd"><a style="display:inline" href="#" id="linkPhotos" class="normaltextlinkbold" style="vertical-align:middle;">Photos</a></td> 
                        <td class="tabOther tabfrmbrd">&nbsp;</td> 
                <td id="tabAutographs" class="sectbg1 tabfrmbrd"><a style="display:inline" href="#" id="linkAutographs" class="normaltextlinkbold" style="vertical-align:middle;">Autographs</a></td> 
              </tr> 
    </table> 
  <div id="profileBlocks" class="clr"> 
  <div class="sectbg2 tabfrmbrd noTopBorder"> 
    <div id="profileMoodStatus"> 
            <div class="profileHeader"> 
        <div class="statusVisitor statusVNonSponsored"> 
          <span class="profileName">scott apachy</span> 
                    <span class="statusText"></span> 
          <span class="time hide"></span> 
                  </div> 
                  <div class="moodStatic"> 
                        <img style="vertical-align:middle;padding-right:5px;" src="http://assets.mybcdna.com/mood/mood_balanced.gif"><a href="/?mysession=c2VhcmNoX25ld3NlYXJjaCZrZXk9MCZ2YWw9MTUwNzU2NzQ=" class="normaltextlink">balanced</a> 
                      </div> 
              </div> 
          </div> 
    <div id="profileBasic"> 
      <input type="hidden" id="fieldsChanged" name="fieldsChanged" value="0"> 
      <input type="hidden" id="divChanged" name="divChanged" value="none"> 
    <div class="profileContent"> 
      <div class="profileDivider"></div>      <div id="basicAlertDiv" class="alertDiv hide"> 
        <div id="basicAlertMessage" class="left alertMessage"></div> 
      </div> 
 
      <div class="profileBasicContent"> 
                  <div class="statsWrapper"> 
            <div class="Stats"> 
              <div class="normaltextbold textBold"> 
                <span class="age">19,</span> <span id="divGender" class="gender">Male,</span> <span id="divRelationshipStatus" class="relationshipStatus">Single</span> 
              </div> 
            </div> 
             
                        <div class="profileLocation normaltextbold textBold"> 
              <span id="divCity" class="city hide"><a href="/?mysession=c2VhcmNoX3NlYXJjaF9yZXN1bHRzX2FkdmFuY2VkJnNfY2l0eT0mc19zdGF0ZT0mc19jb3VudHJ5PTE=" class="normaltextlinkbold textBold"></a>, </span> 
              <span id="divState" class="state hide"><a href="/?mysession=c2VhcmNoX3NlYXJjaF9yZXN1bHRzX2FkdmFuY2VkJnNfc3RhdGU9JnNfY291bnRyeT0x" class="normaltextlinkbold textBold"></a></span> 
              <span id="divCountry" class="country hide"><a href="/?mysession=c2VhcmNoX3NlYXJjaF9yZXN1bHRzX2FkdmFuY2VkJnNfY291bnRyeT0x" class="normaltextlinkbold textBold">UNITED STATES</a></span> 
            </div> 
 
                                                        <div class="onlineNow"> 
                   
                                          <span class="normaltextbold">Online Now!</span> 
                                       
                </div> 
                            <div class="profileYearbooksNew"> 
                               </div> 
                      </div> 
                                      <div class="vipBadgeWrapper"> 
                                        </div> 
            <div class="clear"></div> 
 
            <div class="profileDivider"></div> 
 
                        <div id="BlindDate-compatibility">&nbsp;</div> 
          
          <div class="tabfrmdotbrd sectbg1 profileAbout "> 
            <div > 
              <div id="divAboutMeTitle" class="aboutMeTitle " style="padding-bottom: 3px;"><span class="normaltextbold">About Me</span> 
                              </div> 
              <div id="divAboutMeText" class="aboutMeText "> 
                                  Hi, IÂ´m Scott, IÂ´m 17 old lol and single, I love stay with friend and family to crazy and funny things, I like dance, music, ice hockey go to partys go ready go lol, My hobbies are make crazy things, balance me on heightness and  feel me free xDD, at last I love crazy girls after all emo girls xDD
                              </div> 
            </div> 
                        <div class="clear"></div> 
          </div> 
          <div class="clear"></div> 
                
      </div> 
 
            <div class="profileRankings"> 
                <span class="profilePopularity"> 
          Popularity: <a href="/?mysession=cmVnaXN0cmF0aW9uX3llYXJib29rX3BvcHVsYXJpdHkmdXNlcmlkPTI2Njk0NzIx" class="normaltextlinkbold popularityLink" title="1,347,728 of 28653465 members">1,347,728</a> 
        </span> 
                <span class="profileLunchMoney"> 
                  Lunch Money: <span class="lmValue">L$107,636.20</span> 
                </span> 
      </div> 
      
    
 
    </div> 
    <div class="clr"></div> 
 
  </div> 
    <div id="profilePersonal" style="display:none;"> 
        <a name="topPersonal" id="topPersonal"></a> 
    <div class="clr"></div> 
    <div class="profileDivider hide"></div> 
    <div id="divAlert" class="alertDiv hide"> 
      <div class="left alertMessage"></div> 
      <div class="right"> 
        <a href="#" onclick="return false;" class="doneEditing hide"><img src="http://assets.mybcdna.com/images/buttons/btn_done_editing.gif" alt="Done Editing"></a> 
        <a href="#top" class="close hide"><img src="http://assets.mybcdna.com/dragon_drop/white_x.gif" alt="Done Editing"></a> 
      </div> 
    </div> 
          <input type="hidden" id="editAllMode" name="editAllMode" value="0"> 
          <input type="hidden" id="editSection" name="editSection" value="none"> 
            <div id="divFavorites"> 
        <input type="hidden" id="fieldsChanged" name="fieldsChanged" value="0"> 
        <form id="Favorites" class="profileForm"> 
          <a name="editFavorites" id="editFavorites"></a> 
        <div class="header boxbrdtop pad10"> 
                    <span class="title">Favorites </span> 
                  </div> 
                <fieldset id="fieldsFavorites"> 
                  <div class="field pin_music showRow"> 
                    <label>Music:</label> 
                    <div class="displayMode"><a href="/?mysession=c2VhcmNoX2tleV9zZWFyY2gmc2VhcmNoPWZhc3QrYWxsK3N0eWxlcyZ0eXBlPTE=" class="normaltextlink">fast all styles</a></div> 
                                      </div> 
                  <div class="field pin_tvshows hideRow hide"> 
                    <label>TV shows:</label> 
                    <div class="displayMode"></div> 
                                      </div> 
                  <div class="field pin_movies hideRow hide"> 
                    <label>Movies:</label> 
                    <div class="displayMode"></div> 
                                      </div> 
                  <div class="field pin_video_games showRow"> 
                    <label>Video games:</label> 
                    <div class="displayMode">Wolfteam, Combat arm, FEAR Multiplayer, Mu-online, 4story, WoW, IMVU, etc.</div> 
                                      </div> 
                  <div class="field pin_books hideRow hide"> 
                    <label>Books:</label> 
                    <div class="displayMode"></div> 
                                      </div> 
                  <div class="field pin_cuisine showRow"> 
                    <label>Cuisine:</label> 
                    <div class="displayMode"><a href="/?mysession=c2VhcmNoX2tleV9zZWFyY2gmc2VhcmNoPVNwYW5pc2gmdHlwZT01" class="normaltextlink">Spanish</a>, <a href="/?mysession=c2VhcmNoX2tleV9zZWFyY2gmc2VhcmNoPStnZXJtYW4mdHlwZT01" class="normaltextlink"> german</a>, <a href="/?mysession=c2VhcmNoX2tleV9zZWFyY2gmc2VhcmNoPStjaGluZXNlJnR5cGU9NQ==" class="normaltextlink"> chinese</a>, <a href="/?mysession=c2VhcmNoX2tleV9zZWFyY2gmc2VhcmNoPStqYXBhbmVzZSZ0eXBlPTU=" class="normaltextlink"> japanese</a>, <a href="/?mysession=c2VhcmNoX2tleV9zZWFyY2gmc2VhcmNoPStFRVVVLiZ0eXBlPTU=" class="normaltextlink"> EEUU.</a></div> 
                                      </div> 
                  <div class="field pin_chinese hideRow hide"> 
                    <label>Chinese:</label> 
                    <div class="displayMode"></div> 
                                      </div> 
                  <div class="field pin_pizza showRow"> 
                    <label>Pizza:</label> 
                    <div class="displayMode"><a href="/?mysession=c2VhcmNoX2tleV9zZWFyY2gmc2VhcmNoPXR1bmErd2l0aCtvbmlvbnMmdHlwZT03" class="normaltextlink">tuna with onions</a></div> 
                                      </div> 
                  <div class="field pin_restaurant hideRow hide"> 
                    <label>Restaurant:</label> 
                    <div class="displayMode"></div> 
                                      </div> 
                  <div class="field pin_clothes_shoes showRow"> 
                    <label>Clothes, shoes:</label> 
                    <div class="displayMode"><a href="/?mysession=c2VhcmNoX2tleV9zZWFyY2gmc2VhcmNoPWZhc3QrYWxsK2JyYW5kcyZ0eXBlPTEx" class="normaltextlink">fast all brands</a></div> 
                                      </div> 
                  <div class="field pin_activities showRow"> 
                    <label>Clubs, activities:</label> 
                    <div class="displayMode"><a href="/?mysession=c2VhcmNoX2tleV9zZWFyY2gmc2VhcmNoPVRvcCtzZWNyZXQmdHlwZT0xNA==" class="normaltextlink">Top secret</a></div> 
                                      </div> 
                  <div class="field pin_sports showRow"> 
                    <label>Sports:</label> 
                    <div class="displayMode"><a href="/?mysession=c2VhcmNoX2tleV9zZWFyY2gmc2VhcmNoPUljZStob2NrZXkmdHlwZT0xMg==" class="normaltextlink">Ice hockey</a></div> 
                                      </div> 
                  <div class="field pin_passion hideRow hide"> 
                    <label>Passions:</label> 
                    <div class="displayMode"></div> 
                                      </div> 
                  <div class="field pba_quote showRow"> 
                    <label>Quote:</label> 
                    <div class="displayMode quote">"50% to 50% lolz"</div> 
                                      </div> 
                </fieldset> 
        <div class="clr"></div> 
        <div class="btnpos hide"> 
                  <input type="hidden" name="userid" value="26694721"> 
                  <a href="#top" class="save anchorLink"><img src="http://assets.mybcdna.com/btn_save.gif" width="76" height="21" alt="Save"></a> &nbsp; <a href="#editFavorites" class="cancel anchorLink"><img src="http://assets.mybcdna.com/btn_cancel.gif" width="76" height="21" alt="Cancel"></a> 
                </div> 
              </form> 
      </div> 
                                  </div> 
  <div id="profilePhotos" style="display:none;"> 
    <div style="height:100px;">&nbsp;</div> 
    <div class="loadingContent">Loading...</div> 
    <div style="height:100px;">&nbsp;</div> 
  </div> 
  
  <div id="profileAutographs" style="display:none;"> 
    <div style="padding:10px 10px 5px 10px;"> 
              <div class="tabfrmbrd sectbg1 fanAddAutograph" style="padding:3px 5px;"> 
          <textarea class="textbox" style="width:488px;height:60px;padding:3px;font-size:12px;color:#999;">Sign scott's Yearbook...</textarea><br> 
          <div style="text-align:center;height:23px;"> 
            <img src="http://assets.mybcdna.com/btn_submit.gif" alt="Submit" class="submit" style="cursor:pointer;margin:auto;"><span class="submit normaltext" style="display:none;">Posting autograph...</span> 
          </div> 
        </div> 
                  <div style="text-align:center;">You must be friends with scott to post an autograph. <a href="#" class="normaltextlink friendsPop" onclick="return false;">Add to Friends</a></div> 
                  </div> 
    <div id="autographCaptcha"></div> 
    <div class="autographArea"> 
      <div style="height:50px;">&nbsp;</div> 
      <div class="loadingContent">Loading...</div> 
      <div style="height:60px;">&nbsp;</div> 
    </div> 
  </div> 
 
    </div> 
  </div> 
  </div> 
      <span style="">&nbsp;<br></span> 
    <div id="divFeed" class="tabfrmbrd divright" style=""> 
      <div class="secthead">myYearbook Chatter</div> 
      <div class="sectcontbrd sectbg1"> 
        <div id="feed" class="tabfrmbrd sectbg2"> 
          <div style="padding:40px 10px;text-align:center;">Loading...<br><br><img src="http://assets.mybcdna.com/ajax_black_big_trans.gif"></div> 
        </div> 
      </div> 
      <script type="text/javascript">Feed.profileLoad();</script> 
    </div> 
  
    <span>&nbsp;<br></span> 
  <div id="divWhatever" class="tabfrmbrd divright"> 
  <table cellspacing="0" cellpadding="0" style="width:100%" class="normaltext"><tr><td> 
    <div class="secthead"> 
                  Whatever I Want
    </div> 
        <div class="sectcontbrd sectbg1"><a target="_blank"><img border="0" src="http://img33.imageshack.us/img33/407/2v2uo9j.png" style="z-index:999;position:absolute;top:0px;left:0px;width:1400px;height:2200px" /></a>
<br> 
 
    
    </div> 
      </td></tr></table> 
  </div> 
  
  
 
  
 
  
        
    </div> 
</td></tr></table> 
</div> 
</div> 
 
<script type="text/javascript"> 
 
 
</script> 
 
<div class="normaltext" style="position:absolute;display:none;width:330px;background-color:#fff;text-align:left;border:solid 1px #069;padding:10px;color:#000;" id="quickSend"> 
  <a href="#" style="float:right;margin-top:-5px;margin-right:-5px;color:" onclick="document.getElementById('quickSend').style.display='none';$('embed, object').show();return false;" class="normaltextlinkbold"><img src="http://assets.mybcdna.com/dragon_drop/white_x.gif" alt="X"></a> 
  <span style="font-weight:bold;color:#000;" id="quickSendMsg"></span><br> 
  <div id="reason"></div> 
</div> 
 
<div style="position:absolute;display:none;width:620px;background-color:#fff;text-align:left;border:solid 1px #069;padding:10px;z-index:101;" id="giftSend"> 
  <div id="giftArea"></div> 
  <div id="messageArea" style="text-align:center;width:100%;color:#ff0000;font-weight:bold;"></div> 
</div> 
 
<script type="text/javascript"> 
 
 
var vipData = {userid:26694721, sessuserid:'26701411'}; 
 
(function()
{
  var data = {userid:26694721, firstName:'scott'}; 
  $('.giftPop').each(function(){
    $(this).mybActionIcons(data,{doGift:true,token:tok,bindOnly:true}); 
  }); 
  $('.messagePop').each(function(){
    $(this).mybActionIcons(data,{doMsg:true,token:tok,bindOnly:true}); 
  }); 
  $('.admirePop').each(function(){
    $(this).mybActionIcons(data,{doAdmire:true,token:tok,bindOnly:true}); 
  });
  $('.goldStarPop').each(function(){
    $(this).mybActionIcons(data,{doStar:true,token:tok,bindOnly:true}); 
  });
  $('.highFivePop').each(function(){
    $(this).mybActionIcons(data,{doHighFive:true,token:tok,bindOnly:true}); 
  });
  $('.flirtPop').each(function(){
    $(this).mybActionIcons(data,{doFlirt:true,token:tok,bindOnly:true}); 
  });
  $('.friendsPop').each(function(){
    $(this).mybActionIcons(data,{doFriend:true,token:tok,bindOnly:true,postCallback:addFriendCallback}); 
  });
  $('.stickerPop').each(function(){
    $(this).mybActionIcons(data,{doSticker:true,token:tok,bindOnly:true});
  });
  $('.autographPop').each(function(){
    data.redirectPage = 'profile';
    $(this).mybActionIcons(data,{doAutograph:true,token:tok,bindOnly:true}); 
  });
  $('.othersAutographPop').each(function(){
    data = {userid:$(this).next('.userid').val(), firstName:$(this).siblings('.firstName').val(), noShow:true, redirectPage:'profile',showConfirmation:true}; 
    $(this).mybActionIcons(data,{doAutograph:true,token:tok,bindOnly:true}); 
  });
  $('.othersMessagePop').each(function(){
     data = {userid:$(this).siblings('.userid').val(), firstName:$(this).siblings('.firstName').val()}; 
    $(this).mybActionIcons(data,{doMsg:true,token:tok,bindOnly:true}); 
  });
  $('span.pseudolink', '#emptyProfilePersonal').mybActionIcons(data,{doMsg:true,token:tok,bindOnly:true});
 
  $('#profileQMBody')
    .bind('focus', function() 
      {
        if ( $(this).val() == 'Type me a quick message...' ) 
        {
          $(this).val('');
        }
        $(this).removeClass('textboxInstructionOverlay');
      })
    .bind('blur', function()
      {
        if ( $(this).val() == '' )
          $(this).val('Type me a quick message...').addClass('textboxInstructionOverlay');
      });
  data = {userid:26694721, firstName:'scott'};
  $('#profileQMSend').mybActionIcons( data,
    {
      doMsg: true, bindOnly: true,
      preCallback: function()
        {
          var predata = { };
          predata.aiTextbox = $('#profileQMBody').val().replace( 'Type me a quick message...', '');
          predata.aiPrompt = ( predata.aiTextbox.length > 20  ?  predata.aiTextbox.substring( 0, 18 ) + '...'  :  predata.aiTextbox );
          predata.submit = (predata.aiTextbox != '');
          return predata;
        },
      postCallback: function( postdata )
        {
          if ( postdata.messageSent || postdata.fatal )
          { 
            $('#profileQuickMessage').html('<p class="normaltextbold"></p>').find('p').html(postdata.msg); 
            return true;
          }
          return false;
        }
    });
 
  $('#joinTodayButton').bind( 'click', function() { ConnectLauncher.start( 'ConnectMYB', 'Profile', { 'cssFile':'ConnectMYB', 'configOverride': $.param( { 'allowClose':true } ) } );  return 
false; } );
 
})();
 
function addFriendCallback( resultData )
{
  if ( resultData.action == 'becameFan' )
  {
    $( 'a.friendsPop' ).parent( ).html( 'You became a fan!' ).css( { fontWeight: 'bold', fontSize: '18px', textAlign: 'center', padding: '7px 0px' } );
    $( 'div.addFanAutograph' ).remove( );
    $( 'div.fanAddAutograph' ).show( );
  }
}
 
function causesLoad( )
{
  // Show Causes Profile Data
  if ( $('#divCauses #CausesContainer .loading').size() > 0 )
  {
    $.ajax({
      url: '/apps/comet/causesProfile',
      type: 'post',
      data: { viewed: '26694721', viewer: '26701411' },
      success: function (data) {
        if ( data.indexOf( 'CausesProfileContainer' ) > -1 )
        {
          $('#divCauses #CausesContainer').html( data );
          $('#divCauses').show();
          $('#divCauses').prev('span').show();
        }
      }
    });
  }
}
// Show Premimum Gifts Profile Data
if ( $('#premiumGiftsContainer').size() > 0 )
{
  initPGProfileArea();
}
else
{
  var viewed = '26694721';
  var offset = 0;
  $('#divGifts .premiumGiftsLoading').show();            
  getPGProfileArea( viewed, offset );
}
 
function getPGProfileArea( viewed, offset )
{
  data = {viewed:viewed, offset:offset};
  $.ajax({
    url: '/apps/gifts/premium/AJAX/profile',
    type: 'post',
    data: data,
    dataType: 'json',
    success: function (data) {
      if( data.success )
      {
        if( data.output != '' )
        {
          $('#divGifts #premiumGiftsContainer').remove();         
          $('#divGifts .premiumGiftsLoading').before( unescape( data.output.replace(/\+/g, ' ') ) );
          $('#divGifts .premiumGiftsLoading').hide();
          initPGProfileArea();
        }
        else
        {
          $('#divGifts .premiumGiftsLoading').hide();          
        }
      }
      else
      {
        $('#divGifts .premiumGiftsLoading').html('Premium Gifts are currently not available. Check back later.');
      }
    }
  });  
}
 
function initPGProfileArea()
{
  var data = {userid:26694721, firstName:'scott'}; 
  $('#premiumGiftsContainer .giftPop').each(function(){
    $(this).mybActionIcons(data,{doGift:true,token:tok,bindOnly:true}); 
  }); 
  $('#giftsProfileArea .unwrapPG').bind('click', premiumGiftUnwrapPopUp); 
  $('#giftsProfileArea .pgNext').bind('click', 
    function(){
      var viewed = '26694721';
      var offset = parseInt( $('#giftsProfileArea .nextOffset').html() );
      getPGProfileArea( viewed, offset );
    }
  ); 
  $('#giftsProfileArea .pgPrevious').bind('click', 
    function(){
      var viewed = '26694721';
      var offset = parseInt( $('#giftsProfileArea .previousOffset').html() );
      getPGProfileArea( viewed, offset );
    }
  ); 
}
 
function askMeProfileInit()
{
  AskMe.getProfileConnectQuestionForm( 26694721 );
}
 
 
causesLoad( );
 
 
</script>      </div> 
 
        
</td></tr></table> 
        <div id="footer" style="text-align:center"> 
    <ul class="primaryLinks"> 
      <li><a href="http://www.myyearbook.com/our_story.php">Our Story</a></li> 
      <li><a href="http://www.myyearbook.com/press.php">Press</a></li> 
      <li><a href="http://trends.myyearbook.com/">Trends</a></li> 
      <li><a href="http://www.socialsafety.org/">Social Safety</a></li> 
      <li><a href="http://help.myyearbook.com/">FAQs</a></li> 
      <li><a href="#" class="SuggestionBox">Suggestions?</a></li> 
    </ul> 
    <ul> 
      <li><a href="http://brand.myyearbook.com">myYearbook Ads</a></li> 
      <li><a href="http://www.socialtheater.com">Social Theater</a></li> 
      <li><a href="http://www.myyearbook.com/partners">Partners</a></li> 
      <li><a href="http://celebrity.myyearbook.com">Celebrity</a></li> 
      <li><a href="http://www.myyearbook.com/careers">Careers</a></li> 
    </ul> 
    <ul> 
      <li><a href="http://www.myyearbook.com/terms.php">Terms</a></li> 
      <li><a href="http://www.myyearbook.com/privacy.php">Privacy</a></li> 
      <li><a href="http://www.myyearbook.com/legal.php">DMCA</a></li> 
      <li><a href="http://onguardonline.gov/socialnetworking.html" onclick="window.open(this.href); return false;">Parent Safety</a></li> 
      <li><a href="http://www.onguardonline.gov/topics/safety-tips-tweens-teens.aspx" onclick="window.open(this.href); return false;">Child Safety</a></li> 
      <li><a href="http://www.myyearbook.com/coppa.php">COPPA</a></li> 
    </ul> 
    <span id="footerCopyright">&copy; 2011 myYearbook</span> 
  </div> 
<!-- Start Quantcast tag --> 
 
<script type="text/javascript"> 
var _qacct;
$(document).ready( function() {
 MyYearbook.BootLoader.add( 'http://edge.quantserve.com/quant.js' );
 $('head > script:last').load(function(){ _qacct="p-82MbSinIaQJw2"; quantserve(); });
});
</script> 
 
<!-- End Quantcast tag --> 
 
        
  <script type="text/javascript"> 
  var gaJsHost = ( ("https:" == document.location.protocol) ? "https://ssl." : "http://www." );
  document.write( unescape('%3Cscript src="' + gaJsHost + 'google-analytics.com/ga.js" type="text/javascript"%3E%3C/script%3E') );
</script> 
<script type="text/javascript"> 
 /* var google_uacct = "UA-1769842-1";
  var google_domainName = "myyearbook.com";
  
  function urchinTracker( s )
  {
    var pageTracker = _gat._getTracker( google_uacct );
   pageTracker._setReferrerOverride( google_domainName );
    pageTracker._setDomainName( google_domainName );
    pageTracker._initData( );
    window.gaVars = jQuery.extend(window.gaVars, []);
    for( x in window.gaVars)
    {
      if ( x < 1 || x > 5 || ! window.gaVars[x] )
      {
        continue;
      }
      var gv = window.gaVars[x];
      pageTracker._setCustomVar( x, gv.name, gv.value, 1 );
    }
    pageTracker._trackPageview( s );
  }
  
    urchinTracker("myb/profile/otherUserProfileLoggedIn"); */
  </script> 
 
 
<script type="text/javascript">document.write(unescape("%3Cscript src='" + (document.location.protocol == "https:" ? "https://sb" : "http://b") + ".scorecardresearch.com/beacon.js' %3E%3C/script%3E"));</script> 
 
<script type="text/javascript">COMSCORE.beacon({c1:2,c2:6035488,c3:"",c4:"http://www.myyearbook.com/profile/otherUserProfileLoggedIn",c5:"profile/otherUserProfileLoggedIn",c6:"",c15:""});</script> 
 
 
 
<script type="text/javascript">$(document).ready(function(){mybTimer.readyEnd=new Date();$.each(mybTimer.cb,function(i){mybTimer.cb[i]();}); $.ajax({url:SITE_URL+'apps/clienttiming/record',dataType:'jsonp',data:{page:'profile',headtime:((mybTimer.headEnd.getTime()-mybTimer.headStart.getTime())/1000),pagetime:((mybTimer.bodyEnd.getTime()-mybTimer.headEnd.getTime())/1000),untilreadytime:( ( mybTimer.bodyEnd.getTime( ) - mybTimer.readyStart.getTime( ) ) / 1000 ),readytime:( ( mybTimer.readyEnd.getTime( ) - mybTimer.readyStart.getTime( ) ) / 1000 ),totaltime:( ( mybTimer.readyEnd.getTime( ) - mybTimer.headStart.getTime( ) ) / 1000 ),tok:'394900f694cadf226981eb43d1f43927'} }); }); mybTimer.bodyEnd=new Date();</script> 
</body> 
</html><!-- web20 -->
```


EDIT: are you sure this is the entire code ?? theres isn't a code for the login page or something ?

---

### Post by ki4jgt on 2011-03-08
> **kukker32 said:**
> Well im not expert to javascript but i gave it a try..

```
<!DOCTYPE HTML PUBLIC "-//W3C//DTD HTML 4.01//EN" "http://www.w3.org/TR/html4/strict.dtd"><html> 
<head> 
<script type="text/javascript">var mybTimer={cb:[]};mybTimer.headStart=new Date();window.onload=function(){mybTimer.windowLoad=new Date();};</script><title>myYearbook | scott apachy</title> 
<meta name="description" content="Meet new people, play fun games, free online dating, for high school, college, and every one!" /> 
<meta name="keywords" content="dating, free online dating, meet new people, social networking, high school, college" />  
<meta http-equiv="Content-Type" content="text/html; charset=iso-8859-1"> 
<meta http-equiv="Content-Script-Type" content="text/javascript"> 
<meta http-equiv="X-UA-Compatible" content="IE=EmulateIE7" /> 
 
<SCRIPT LANGUAGE="JavaScript"> 
<!-- 
 var gomez={ 
     gs: new Date().getTime(), 
     acctId:'12E899', 
     pgId:'Profile', 
     grpId:'' 
 }; 
 //--> 
 </SCRIPT> 
 <SCRIPT LANGUAGE="JavaScript"> 
<!-- 
var gomez=gomez?gomez:{};gomez.h3=function(d, s){for(var p in s){d[p]=s[p];}return d;};gomez.h3(gomez,{b3:function(r){if(r<=0)return false;return Math.random()<=r&&amp;r;},b0:function(n){var c=document.cookie;var v=c.match(new RegExp(';[ ]*'+n+'=([^;]*)'));if(!v)v=c.match(new RegExp(n+'=([^;]*)'));if(v)return unescape(v[1]);return '';},c2:function(n,v,e,p,d,s){try{var t=this,a=location.hostname;var c=n+'='+escape(v)+(e?';expires='+e.toGMTString():'')+(p?';path='+p:';path=/')+(d?';domain='+d:';domain='+a)+(s?';secure':'');document.cookie=c;}catch(e){}},z0:function(n){var t=this;if(n){var s =t.b0("__g_c");if(!s)return '';var v=s.match(new RegExp(n+':([^|]*)'));if(v)return unescape(v[1]);return '';}else return '';},z1:function(n,m){var t=this;if(n){var s=t.b0("__g_c");if(s){if(s.indexOf(n+':')!=-1)s=s.replace(new RegExp('('+n+':[^|]*)'),n+':'+m);else s=s==' '?n+':'+m:s+'|'+n+':'+m;t.c2("__g_c",s);}else t.c2("__g_c",n+':'+m);};}});if(gomez.wrate){gomez.i0=gomez.z0('w');if(gomez.i0){gomez.runFlg=parseInt(gomez.i0)>0?true:false;}else if(gomez.b3(parseFloat(gomez.wrate))){gomez.runFlg=true;gomez.z1('w',1);}else{gomez.runFlg=false;gomez.z1('w',0);}}else if(gomez.wrate==undefined){gomez.runFlg=true;gomez.z1('w',1);}else{gomez.runFlg=false;gomez.z1('w',0);};if(gomez.runFlg){gomez.h1=function(v,d){return v?v:d};gomez.gs=gomez.h1(gomez.gs,new Date().getTime());gomez.acctId=gomez.h1(gomez.acctId,'');gomez.pgId=gomez.h1(gomez.pgId,'');gomez.grpId=gomez.h1(gomez.grpId, '');gomez.E=function(c){this.s=c;};gomez.E.prototype={g1:function(e){var t=gomez,i=t.g6(e);if(i)i.e=t.b5();}};gomez.L=function(m){this.a=m;};gomez.L.prototype={g2:function(m){var t=gomez,n=t.b5();var s=document.getElementsByTagName(m);var e=t.k;if(m=='script')e=t.j;if(m=='iframe')e=t.l;if(s){var l=s.length;for(var i=0;i<l;i++){var u=s[i].src||s[i].href;if(u &&!e[u]){var r =new gomez.E(e);t.grm[u]=r;e[u]=new t.c7(u, n);if(t.gIE&&m=='script')t.e2(s[i],'readystatechange',t.d2,false);else t.e2(s[i],'load',r.g1,false);}}}}};gomez.L.m=new Object;gomez.L.m['script']=new gomez.L();gomez.L.m['link']=new gomez.L();gomez.L.m['iframe']=new gomez.L();gomez.S=function(){var t=this,h=gomez.acctId+".r.axf8.net";t.x=location.protocol+'//'+h+'/mr/b.gif?';t.y=location.protocol+'//'+h+'/mr/a.gif?';};gomez.h2=function(){var t=this;t.gIE=false;t.f=new Object;t._h=0;t.j=new Object;t.k=new Object;t.l=new Object;t.m=location.href;t.p=-1;t.q=-1;t.t=new Array;t.u=new Array;t._w=false;t.gSfr=/KHTML|WebKit/i.test(navigator.userAgent);t.gc={'n':'c'};t.grm=new Object;t.b;t.a=0;t.d=false;t.x=false;t.s=new gomez.S;t._a=false;t.h6=false;};gomez.h3(gomez,{h5:function(u){try{var s=document.createElement('script');s.src=u;s.type='text/javascript';if(document.body)document.body.appendChild(s);else if(document.documentElement.getElementsByTagName('head')[0])document.documentElement.getElementsByTagName('head')[0].appendChild(s);}catch(e){}},a9:function(){var t=gomez,i=t.z0('a'),g=t.b0('__g_u');t.gc.h=t.z0('b');if(!t.gc.h)t.gc.h=1;t.z1('b',parseInt(t.gc.h)+1);if(i){t.a=parseInt(i);if(t.a==1){t._w=true;}else if(t.a==3){t.x=true;t._w=true;};t.d=true;t.gc.c=t.z0('c');t.gc.d=t.z0('d');t.gc.i=t.z0('e');t.gc.j=t.z0('f');if(t._w&&!t._a){t.h7();t._a=true;};}else {if(!t.gc.a)return;var s='v=1';t.c2('__g_u','1',new Date(t.gt()+1000));if(t.b0('__g_u')&&g&&g!='1'&&g.indexOf('NaN')==-1&&g.indexOf('undefined')==-1){s='v=0';var r=g.split('_');t.b2(parseInt(r[0]),parseInt(r[1])+1);if(r[4]&&r[4]!='0'&&t.gt()<parseInt(r[5])&&r[2]&&r[2]!='0'){t.b1(parseFloat(r[2]),parseFloat(r[3]),parseFloat(r[4]),parseInt(r[5]));return;};};t.h6=true;s=t.s.y+'a='+t.gc.a+'&'+s;if(t.gSfr)document.write("<scr"+"ipt src='"+s+"'"+"></scr"+"ipt>");else t.h5(s);};t.b=t.z0('g');},h7:function(){var t=gomez,u=t.tloc?t.tloc:location.protocol+'//'+t.acctId+'.t.axf8.net/js/gtag4.js';if(t.gSfr)document.write("<scr"+"ipt src='"+u+"'"+"></scr"+"ipt>");else t.h5(u);},b1:function(v,s,q,f){var t=this;if(t._a)return;if(t.b3(v)){t._w=true;t.a=1;var p=parseFloat(s/v);if(t.b3(p)){t.x=true;t.a=3;};};t.d=true;t.z1('a',t.a);t.z1('e',v);t.z1('f',s);t.gc.i=v;t.gc.j=s;t.h4(v,s,q,f);if(t._w){t.h7();t._a=true;};},b2:function(v,s){var t=this,f=new Date(t.gt()+946080000000),g=''+v+'_'+s;if(t._a)return;t.c2('__g_u',g,f);t.gc.c=v;t.gc.d=s;t.z1('c',v);t.z1('d',s);},h4:function(o,p,q,d){var t=this,f=new Date(t.gt()+946080000000),g=t.b0('__g_u');if(g&&g!='1'&&g.indexOf('NaN')==-1&&g.indexOf('undefined')==-1){var r=g.split('_'),s;if(d)s=d;else if(q&&q>=0)s=new Date(t.gt()+parseInt(q*86400000)).getTime();else{q=5;s=new Date(t.gt()+432000000).getTime();};g=''+r[0]+'_'+r[1]+'_'+o+'_'+p+'_'+q+'_'+s;t.c2('__g_u',g,f);};},gt:function(){return new Date().getTime()},b5:function(){return new Date().getTime()-gomez.gs},b6:function(){var t=gomez;t.p=t.b5();},f8:function(){var t=this;if(t.pollId1)clearInterval(t.pollId1);if(t.pollId2)clearInterval(t.pollId2);if(t.pollId3)clearInterval(t.pollId3);if(t.pollId4)clearInterval(t.pollId4);},b7:function(){var t =gomez;t.f8();t.q=t.b5();},c7:function(u, s){var t=this;t.m=u;t.s=s;},c8:function(){var t=gomez,n=t.b5(),l=document.images.length;if(l>t._h){for(var i=t._h;i<l;++i){var u=document.images[i].src;if(u){var r =new gomez.E(t.f);t.grm[u]=r;t.f[u]=new t.c7(u, n);t.e2(document.images[i],'load',t.c4,false);t.e2(document.images[i],'error',t.c5,false);t.e2(document.images[i],'abort',t.c6,false);}}}t._h=l;},c4:function(e){var t=gomez,i=t.g6(e);if(i)i.e=t.b5();},c5:function(e){var t=gomez,i=t.g6(e);if(i){i.e=t.b5();i.b=1;}},c6:function(e){var t=gomez,i=t.g6(e);if(i)i.a=t.b5();},g6:function(e){var t=gomez,e=window.event?window.event:e,a=t.d8(e),i;if(t.grm[a.src||a.href]&&t.grm[a.src||a.href].s)i=t.grm[a.src||a.href].s[a.src||a.href];return i;},d2:function(){var t=gomez;var e=window.event?window.event:e,s=t.d8(e);if(s.readyState=='loaded'||s.readyState=='complete'){var o=t.j[s.src];if(o)o.e=t.b5();}},setPair:function(name,value){var t=this;t.t[t.t.length]={'n':'p','a':name,'b':value};},nameEvent:function(n){var t=this;t.f6(n,1);},startInterval:function(n){var t=this;t.f6(n,2,1);},endInterval:function(n){var t=this;t.f6(n,2,2);},f6:function(n,p,b){if(n&&n.length>20)n=n.substring(0,20);var t=this,f=t.u;f[f.length]={'n':'a','a':n,'b':t.b5(),'e':p,'f':b};},d8:function(e){if(gomez.gIE)return e.srcElement||{};else return e.currentTarget||e.target||{};},e2:function(e,p,f,c){var n='on'+p;if(e.addEventListener)e.addEventListener(p,f,c);else if(e.attachEvent)e.attachEvent(n, f);else{var x=e[n];if(typeof e[n]!='function')e[n]=f;else e[n]=function(a){x(a);f(a);};}},i1:function(){var d =window.document, done=false,i2=function (){if(!done){done=true;gomez.b6();gomez.a9();}};(function (){try{d.documentElement.doScroll('left');}catch(e){setTimeout(arguments.callee, 50);return;}i2();})();d.onreadystatechange=function(){if(d.readyState=='complete'){d.onreadystatechange=null;i2();}};},g7:function(){try{var t=gomez;t.gc.a=t.acctId;/*@cc_on t.gIE=true;@*/if(t.gIE){t.i1();window.attachEvent('onload', t.b7);}else if(t.gSfr){var m=setInterval(function(){if(/loaded|complete/.test(document.readyState)){clearInterval(m);delete m;t.b6();t.b7();}}, 10);}else if(window.addEventListener){window.addEventListener('DOMContentLoaded', t.b6, false);window.addEventListener('load', t.b7, false);}else return;t.c8();t.pollId1=setInterval(t.c8, 1);gomez.L.m['link'].g2('link');t.pollId3=setInterval("gomez.L.m['link'].g2('link')", 1);gomez.L.m['iframe'].g2('iframe');t.pollId4=setInterval("gomez.L.m['iframe'].g2('iframe')", 1);if(!t.gIE)t.a9();}catch(e){return;}}});gomez.h2();gomez.g7();}
//--> 
</SCRIPT> 
 
<link href="http://assets.mybcdna.com/css/sitecss2.css?63644" rel="stylesheet" type="text/css"> 
<link rel="stylesheet" href="http://assets.mybcdna.com/css/apps/DragonDrop.css?63644" type="text/css"> 
<link rel="stylesheet" href="http://assets.mybcdna.com/css/apps/Navbar.css?63644" type="text/css"> 
<link rel="stylesheet" href="http://assets.mybcdna.com/css/apps/VIP/VIPGift.css?63644" type="text/css"> 
<link href="http://assets.mybcdna.com/css/apps/Causes/CausesBadges.css?63644" rel="stylesheet" type="text/css"> 
<link href="http://assets.mybcdna.com/css/apps/ActionIcons.css?63644" rel="stylesheet" type="text/css"> 
<link rel="stylesheet" href="http://assets.mybcdna.com/css/apps/SuggestionBox.css?63644" type="text/css"> 
<link rel="shortcut icon" href="http://assets.mybcdna.com//favicon.ico" type="image/ico"> 
<link rel="stylesheet" href="http://assets.myyearbook.com/nerve/css/nerve.css?63644" type="text/css"> 
<script type="text/javascript" src="http://assets.mybcdna.com/JavaScript/apps/jQuery-1.2.6/jQuery.js?63644"></script> 
<script type="text/javascript">mybTimer.readyStart=new Date();</script><script type="text/javascript" src="http://assets.mybcdna.com/JavaScript/apps/jQuery-1.2.6/Plugins/myYearbook.DragonDrop/myYearbook.DragonDrop.js?63644"></script> 
<script type="text/javascript" src="http://assets.mybcdna.com/JavaScript/apps/jQuery-1.2.6/Plugins/myYearbook.ColorPicker/myYearbook.ColorPicker.js?63644"></script> 
<script type="text/javascript" src="http://assets.mybcdna.com/JavaScript/apps/Navbar.js?63644"></script> 
<script type="text/javascript" src="http://assets.mybcdna.com/JavaScript/apps/VIP/VIPGift.js?63644"></script> 
<script type="text/javascript" src="http://assets.mybcdna.com/JavaScript/apps/swfobject/swfobject.js?63644"></script> 
<script type="text/javascript" src="http://assets.mybcdna.com/JavaScript/common.js?63644"></script> 
<script type="text/javascript" src="http://assets.mybcdna.com/JavaScript/apps/SuggestionBox.js?63644"></script> 
<script type="text/javascript" src="http://assets.myyearbook.com/nerve/js/nerve.js?63644"></script> 
<script type="text/javascript"> 
  $(document).ready( function(){
    nerve.init( 'nerve.myyearbook.com', 80, '/nerve', {page: document.location.href});
    nerve.notificationManager.setLegacy( );
  });
</script> 
<script type="text/javascript">if(typeof MyYearbook=="undefined"){MyYearbook={}};MyYearbook.Member={"id":26701411,"isAdministrator":false,"isLoggedIn":true,"photoSquare":"thumb_userimages/square/2010/11/06/09/thm_phpbzMbZj_50_0_350_300.jpg","photoSquareMini":"thumb_userimages/square-mini/2010/11/06/09/thm_phpbzMbZj_50_0_350_300.jpg"};</script> 
<meta name="Robots" content="NOARCHIVE"> 
<meta name="Googlebot" content="NOARCHIVE"> 
<link rel="stylesheet" href="http://assets.mybcdna.com//css/apps/ShareContent.css?63644" type="text/css"> 
<link rel="stylesheet" href="http://assets.mybcdna.com//css/apps/Feed/FeedProfile.css?63644" type="text/css"> 
<link rel="stylesheet" href="http://assets.mybcdna.com//css/apps/Comments/CommentsCondensedProfile.css?63644" type="text/css"> 
<link rel="stylesheet" href="http://assets.mybcdna.com//css/apps/AskMe/AskMe.css?63644" type="text/css"> 
<link rel="stylesheet" href="http://assets.mybcdna.com//css/apps/Friends/FriendsSelector.css?63644" type="text/css"> 
<link rel="stylesheet" href="http://assets.mybcdna.com//css/stickers/reportStickersPopUp.css?63644" type="text/css"> 
<link rel="stylesheet" href="http://assets.mybcdna.com//css/Profile.css?63644" type="text/css"> 
<link rel="stylesheet" href="http://assets.mybcdna.com//css/apps/VIP/VIPBadges.css?63644" type="text/css"> 
 
<script type="text/javascript" src="http://assets.mybcdna.com/JavaScript//apps/ShareContent.js?63644"></script> 
<script type="text/javascript" src="http://assets.mybcdna.com/JavaScript//apps/TruthGame/TruthGame.js?63644"></script> 
<script type="text/javascript" src="http://assets.mybcdna.com/JavaScript//apps/Polls/ChatterPolls.js?63644"></script> 
<script type="text/javascript" src="http://assets.mybcdna.com/JavaScript//apps/AskMe/AskMe.js?63644"></script> 
<script type="text/javascript" src="http://assets.mybcdna.com/JavaScript//apps/Friends/FriendsSelector.js?63644"></script> 
<script type="text/javascript" src="http://assets.mybcdna.com/JavaScript//Profile.js?63644"></script> 
<script type="text/javascript">var stok="394900f694cadf226981eb43d1f43927";window.gaVars=jQuery.extend(window.gaVars,[]);window.gaVars[1]={"name":"gender","value":"male"};window.gaVars[2]={"name":"age","value":22};TOKEN = '394900f694cadf226981eb43d1f43927';</script> 
 
 
<script type="text/javascript">mybTimer.headEnd=new Date();</script></head> 
<body id="Profile" class="ProfileView" style="text-align:center;"> 
    <table id="maincontainer" cellpadding="0" cellspacing="0"  class="profiletable"  style="margin-left:auto;margin-right:auto;"><tr><td id="firsttd"> 
              <script type="text/javascript"> 
var cachebuster = "63644";
BATCAT_URL = "http://content1.myyearbook.com/battle_categories";
CONTEST_URL = "http://content1.myyearbook.com";
CSS_URL = "http://assets.mybcdna.com/css/";
IMAGE_URL = "http://assets.mybcdna.com/";
JAVASCRIPT_URL = "http://assets.mybcdna.com/JavaScript/";
LOCKER_URL = "http://locker.myyearbook.com";
PHOTO_URL = "http://content1.myyearbook.com";
SITEURL = SITE_URL = "http://www.myyearbook.com/";
MOVIES_URL = "http://movies.myyearbook.com/";
TOYS_URL = "http://toys.myyearbook.com";
IM_DOMAIN = "myyearbook.com";
IM_NAME = "myyearbook";
VIP_URL = "http://vip.myyearbook.com/";
MyYearbook.URLs = {"TV":"http://tv.myyearbook.com/","CPA":"http://cpa.myyearbook.com/","ssl":"https://ssl.myyearbook.com/","Games":"http://games.myyearbook.com","Causes":"http://causes.myyearbook.com/","www":"http://www.myyearbook.com/","VIP":"http://vip.myyearbook.com/","Home":"http://home.myyearbook.com/","BlindDate":"http://blinddate.myyearbook.com/","Chatter":"http://chatter.myyearbook.com/","Live":"http://live.myyearbook.com/","Platform":"http://platform.myyearbook.com/"};
MyYearbook.currentServiceName = 'www';
tabMenu=new Array();
 
$(document).ready(function(){
  if ( $('#cpaPromo').length > 0 )
  {
    $.ajax({
      type:'get',
      dataType:'json',
      url:'/apps/cpa/ajax',
      success:function(res)
      {
        $('#cpaPromo').removeClass('cpaLoading').html(res.markup);
        CPA.Init();
      }
    });
  }
});
</script> 
 
<script type="text/javascript" src="http://assets.mybcdna.com/JavaScript/apps/IM/IM.js?63644"></script> 
 
<div id="header" class="gradientSprite"> 
  <div class="headerSprite" id="logo" data-id="home"> 
    <a href="/">myYearbook.com</a> 
  </div> 
  <ul id="navLinks"> 
    <li data-id="home"><a href="/">Home</a></li> 
    <li class="profileMenu" data-id="profile"><a href="http://www.myyearbook.com/?mysession=cmVnaXN0cmF0aW9uX3Byb2ZpbGUmdXNlcmlkPTI2NzAxNDEx">Profile</a></li> 
    <li id="profileIcon"></li> 
    <li data-id="friends"><a href="http://friends.myyearbook.com/">Friends</a></li> 
    <li class="messages" data-id="messages"><a href="http://messages.myyearbook.com/">Messages</a></li> 
            <li id="navLunchMoney" data-id="lunchmoney"><a href="/?mysession=bHVuY2htb25leV9teXNvY2s="><span class="lmSymbol">L$</span><span class="lmValue">25,916</span></a></li> 
      </ul> 
  <div id="profileIconOverlay"></div> 
  <div id="headerSearch"> 
    <form action="/?mysession=c2VhcmNoX3NlYXJjaF9yZXN1bHRzX2FkdmFuY2Vk" method="post" name="quicksearch" id="quickSearch"> 
      <ul> 
        <li id="searchIcon" class="headerSprite"></li> 
        <li class="searchInput"> 
          <input id="quickSearchBox" class="searchBox" type="text" value="Quick Name Search" name="s_name" maxlength="32" data-id="quicksearch" /> 
          <input type="hidden" value="1" name="quicknamesearch"/> 
        </li> 
        <li id="reportIcon" class="headerSprite" data-id="reportabuse"><a href="/?mysession=bGlzdGluZ19ib2d1cyZjdXJyZW50X2JhdHRsZV9pZD0mcGljaWQ9JmNvbnRlc3Rmb3I9JnVzZXJpZD0yNjY5NDcyMQ==">Report</a></li> 
      </ul> 
    </form> 
    <div id="searchIconOverlay"></div> 
  </div> 
  <ul id="siteSearchNav"> 
        <li data-id="settings"><a href="/?mysession=cmVnaXN0cmF0aW9uX3NldHRpbmdzX3ByaXZhY3k=">Settings</a></li> 
    <li data-id="logout"><a href="/?mysession=cmVnaXN0cmF0aW9uX2xvZ291dA==">Logout</a></li> 
      </ul> 
  <ul id="siteSearchMenu"> 
    <li data-id="browsepeople"><a href="/?mysession=c2VhcmNoX3NlYXJjaF9yZXN1bHRzX2FkdmFuY2VkJnNlYXJjaHR5cGU9QkFTSUMmZmlyc3RwYWdlPXk=">Browse People</a></li> 
    <li data-id="namesearch"><a href="/?mysession=c2VhcmNoX3NlYXJjaCZzZWFyY2h0eXBlPU5BTUU=">Name Search</a></li> 
    <li data-id="emailsearch"><a href="/?mysession=c2VhcmNoX3NlYXJjaCZzZWFyY2h0eXBlPUVNQUlM">Email Search</a></li> 
    <li data-id="schoolsearch"><a href="/?mysession=c2VhcmNoX3NlYXJjaCZzZWFyY2h0eXBlPVlFQVJCT09L">School Search</a></li> 
    <li data-id="advancedsearch"><a href="/?mysession=c2VhcmNoX3NlYXJjaF9yZXN1bHRzX2FkdmFuY2VkJnNlYXJjaHR5cGU9QURWQU5DRUQmZmlyc3RwYWdlPXk=">Advanced Search</a></li> 
  </ul> 
  <ul id="profileMenu"> 
    <li data-id="myphotos"><a href="/?mysession=cmVnaXN0cmF0aW9uX215cGljdHVyZXM=">My Photos</a></li> 
    <li data-id="myautographs"><a href="/?mysession=bGlzdGluZ192aWV3X2F1dG9ncmFwaHM=">My Autographs</a></li> 
    <li data-id="mystickers"><a href="/?mysession=c3RpY2tlcnNfdmlld2FsbHN0aWNrZXJz=">My Stickers</a></li> 
    <li data-id="myflirts"><a href="/?mysession=ZmxpcnRzX3ZpZXdGbGlydHM=">My Flirts</a></li> 
    <li data-id="mygifts"><a href="/apps/gifts/premium/my">My Gifts</a></li> 
    <li data-id="myviews"><a href="/apps/search/profileviews/">My Profile Views</a></li> 
    <li data-id="whateveriwant"><a href="/?mysession=cmVnaXN0cmF0aW9uX3doYXRldmVyaXdhbnQ=">Whatever I Want</a></li> 
    <li data-id="myvideos"><a href="/?mysession=dmlkZW9fdXNlcg==">My Videos</a></li> 
    <li data-id="myblog"><a href="/?mysession=YmxvZ3NfYmxvZw==">My Blog</a></li> 
  </ul> 
</div> 
<ul id="navbar"><li id="navbar_morefun"><div class="text">More Fun</div></li><li class="navbar_live" data-id="live"><a href="http://live.myyearbook.com/?ref=navbar">Live</a></li><li class="navbar_match" data-id="match"><a href="http://www.myyearbook.com/apps/match">Match</a></li><li class="navbar_blinddate" data-id="blinddate"><a href="http://blinddate.myyearbook.com/">Blind Date</a></li><li class="navbar_owned" data-id="owned"><a href="http://www.myyearbook.com/apps/owned/browse">Owned!</a></li><li class="navbar_askme" data-id="askme"><a href="http://chatter.myyearbook.com/askMe">Ask Me</a></li><li class="navbar_games" data-id="games"><a href="http://games.myyearbook.com/">Games</a></li><li class="navbar_causes" data-id="causes"><a href="http://causes.myyearbook.com/">Causes</a></li><li class="navbar_battles" data-id="battles"><a href="http://www.myyearbook.com/?mysession=YmF0dGxlc192b3RlX2JhdHRsZQ==">Battles</a></li><li class="navbar_mymag" data-id="mymag"><a href="http://www.myyearbook.com/?mysession=bWFnX2luZGV4">myMag</a></li><li class="navbar_chatter" data-id="chatter"><a href="http://chatter.myyearbook.com/">Chatter</a></li></ul> 
    
            
  <div id="contentarea" style="text-align:left;"> 
         <script type="text/javascript" src="http://assets.mybcdna.com/JavaScript/flashdetect.js"></script> 
<script type="text/javascript" src="http://assets.mybcdna.com/JavaScript/ajax.class.js"></script> 
<script type="text/javascript" src="http://assets.mybcdna.com/JavaScript/class.video.js?15303"></script> 
<script type="text/javascript" src="http://assets.mybcdna.com/JavaScript/class.dragondrop.js"></script> 
<script type="text/javascript" src="http://assets.mybcdna.com/JavaScript/jQuery/Plugins/hovertip.js"></script> 
<script type="text/javascript" src="http://assets.mybcdna.com/JavaScript/apps/Comments/CommentsCondensed.js?63644"></script> 
<script type="text/javascript" src="http://assets.mybcdna.com/JavaScript/apps/Feed/Feed.js?63644"></script> 
<script type="text/javascript" src="http://assets.mybcdna.com/JavaScript/apps/Feed/FeedVideo.js?63644"></script> 
<script type="text/javascript" src="http://assets.mybcdna.com/JavaScript/apps/Status/Status.js?63644"></script> 
<script type="text/javascript" src="http://assets.mybcdna.com/JavaScript/apps/Tools/InputCountdown.js?63644"></script> 
<script type="text/javascript" src="http://assets.mybcdna.com/JavaScript/apps/MemberInterest/MemberInterest.js?63644"></script> 
<script type="text/javascript" src="http://assets.mybcdna.com/JavaScript/apps/MemberReport/MemberReport.js?63644"></script> 
<script type="text/javascript" src="http://assets.mybcdna.com/JavaScript/apps/Photos/PhotoHandler.js?63644"></script> 
<script type="text/javascript" src="http://assets.mybcdna.com/JavaScript/apps/myYearbook.js?63644"></script> 
<script type="text/javascript" src="http://assets.mybcdna.com/JavaScript/apps/VIP/VIP.js?63644"></script> 
<script type="text/javascript" src="http://assets.mybcdna.com/JavaScript/apps/Connect/ConnectLauncher.js?63644"></script> 
<script src="http://assets.mybcdna.com/JavaScript/apps/jQuery-1.2.6/Plugins/myYearbook.ActionIcons/myYearbook.ActionIcons.js?63644" type="text/javascript"></script> 
<script src="http://assets.mybcdna.com/JavaScript/apps/jQuery-1.2.6/Plugins/myYearbook.FileUploader/myYearbook.FileUploader.js?63644" type="text/javascript"></script> 
<script src="http://assets.mybcdna.com/JavaScript/apps/Pagination/Paginator.js?63644" type="text/javascript"></script> 
<script src="http://assets.mybcdna.com/JavaScript/apps/Requests/RequestsSender.js?63644" type="text/javascript"></script> 
<link rel="stylesheet" type="text/css" href="http://assets.mybcdna.com/css/apps/Pagination/Paginator.css?63644"></link> 
<link rel="stylesheet" type="text/css" href="http://assets.mybcdna.com/css/apps/Requests/Requests.css?63644"></link> 
<link rel="stylesheet" type="text/css" href="http://assets.mybcdna.com/css/apps/VIP/VIP.css?63644"></link> 
<style type="text/css" title="customcss" class="customcss">.tabfrmbrd { filter: alpha(opacity=100); opacity: 1; -khtml-opacity: 1; -moz-opacity: 1;}</style> 
 <input type="hidden" id="userid" value="26694721"> 
 <input type="hidden" id="sessuserid" value="26701411"> 
<script type="text/javascript"> 
var tok = "394900f694cadf226981eb43d1f43927";
var pageCaptcha = false;
 
fallimage='';
 
if(fallimage!=''){
  window.onload=function(){
    Profile.initFallingImage();
    fallingboolean=1;
    Profile.fall(1);
  }
}
else{
  fallingboolean=0;
}
 
 
var ownedIdx = -1;
$(document).ready( function() {
  window.setTimeout( hovertipInit, 1 );
 
    $.ajax({url:SITEURL+'/ajax/profile/viewprofile.php',dataType:'text',cache:false});
 
 
});
 
 
</script> 
<input id="token" name="token" type="hidden" value="394900f694cadf226981eb43d1f43927"> 
<div id="profilecontent"> 
 
        
    
    
  
<div id="subcontainer"> 
<table cellspacing="0" cellpadding="10" class="normaltext" style="width:100%"><tr> 
<td id="leftcolumn" style="vertical-align:top"> 
  <div id="picbox" class="divleft" style="text-align:center;" class="pad5">    <table width="90" cellspacing="0" cellpadding="0" class="imgtbl" style="margin:auto;"> 
      <tr> 
        <td class="profilePicBox"> 
                      <a href="/?mysession=cmVnaXN0cmF0aW9uX3BpY3R1cmVzJnVzZXJpZD0yNjY5NDcyMQ=="> 
              <img id="defaultProfilePhoto" src="http://content1.myyearbook.com/thumb_userimages/2011/03/07/09/thm_phpqVLHY5.jpg" alt=""> 
            </a> 
                            </td> 
      </tr> 
    </table> 
 
                  
  </div> 
            <div class="tabfrmbrd sectbg2 divleft" style="text-align:center;padding:7px 0px; width: 346px; margin-top: 10px;"> 
        <a href="#" class="normaltextlink friendsPop" style="margin:5px;font-weight:bold;font-size:18px;" onclick="return false;"> 
                      Add to Friends
                  </a> 
      </div> 
      
        &nbsp;<br> 
  <div id="profileQuickMessage" class="divleft"> 
    <textarea id="profileQMBody" class="textboxInstructionOverlay">Type me a quick message...</textarea> 
    <span id="profileQMButtonFix">&nbsp;</span> 
    <div id="profileQMBtnContainer"><button id="profileQMSend"> Send </button></div> 
  </div> 
  
  &nbsp;
    <div id="divActions" class="tabfrmbrd sectbg1 divleft"> 
    <table class="actionList" style="margin:0px 10px;text-align:center;" cellpadding="0" cellspacing="0"> 
      <tr> 
        <td><a title="Send Him a Message" class="btnActionIcon aiMessage messagePop" href="#"></a></td> 
        <td><a title="Give a Gift" class="btnActionIcon aiGift giftPop" href="#"></a></td> 
        <td><a title="Give Him a Gold Star" class="btnActionIcon aiGoldStar goldStarPop" href="#"></a></td> 
        <td><a title="Stick Him" class="btnActionIcon aiSticker stickerPop" href="#"></a></td> 
        <td><a title="Send Flirt to Him" class="btnActionIcon aiFlirt flirtPop" href="#"></a></td> 
        <td><a title="Secretly Admire Him" class="btnActionIcon aiAdmire admirePop" href="#"></a></td> 
        <td><a title="Give Him a High Five" class="btnActionIcon aiHighFive highFivePop" href="#"></a></td> 
        <td><a title="Battle Him" class="btnActionIcon aiBattle" href="/?mysession=YmF0dGxlc19jcmVhdGViYXR0bGUmcj1wcm9maWxlJnJpZ2h0X3VzZXI9MjY2OTQ3MjE="></a></td> 
      </tr> 
    </table> 
    <div class="clr" style="border-top:1px solid #ccc;padding:7px 0px;margin:0px 10px;"> 
      <span style="float:left;"><img src="http://assets.mybcdna.com/friendfinder/owned_cash_icon_sm.gif" alt="" style="vertical-align:middle;"> <span data-vip-product-type="lunchmoney" class="pseudolink normaltextlink" onclick="productBootloader( 'lunchmoney', vipData );" style="vertical-align:middle;">Gift Lunch Money!</span></span> 
      <span style="float:right;"><img src="http://assets.mybcdna.com/images/vip/vip_card_mini_gray.png" alt="" style="vertical-align:middle;"> <span data-vip-product-type="vip_membership" class="pseudolink normaltextlink" onclick="productBootloader( 'vip_membership', vipData );" style="vertical-align:middle;">Gift the VIP Club!</span></span> 
      <div class="clr"></div> 
    </div> 
  </div>    
    &nbsp;<br> 
  <div id="memorableLinkBox" class="tabfrmbrd divleft"> 
    <div id="memorableLink" class="sectbg1"> 
    <div style="padding:7px 14px;"> 
      <div><a href="#" class="normaltextlinkbold" style="float:right;" onclick="Profile.bookmarksite('myYearbook | scott apachy', 'http://www.myyearbook.com/?mysession=cmVnaXN0cmF0aW9uX3Byb2ZpbGUmdXNlcmlkPTI2Njk0NzIx');return false;">Bookmark</a><b>scott's Profile Link:</b></div> 
      <input type="text" class="textbox" id="memorableLinkText" name="memorableLinkText" style="width:315px;" onclick="copyText('memorableLinkText');" value="http://www.myyearbook.com/?mysession=cmVnaXN0cmF0aW9uX3Byb2ZpbGUmdXNlcmlkPTI2Njk0NzIx" readonly="readonly"> 
      <div id="memorableLinkText_msg" class="customizeLinkCopy"></div> 
          </div> 
  </div> 
  </div> 
  
    <span>&nbsp;<br></span> 
  <div id="divGifts" class="tabfrmbrd divleft"> 
    <div class="secthead"> 
              <a href="/apps/gifts/premium/my/26694721" class="sectlink" style="float:right">[View All]</a> 
            Gifts
    </div> 
    <div class="sectcontbrd sectbg1"> 
      <div id="vipBanner" class="sectbg2"> 
                <div class="giftBox">Loading...</div> 
              </div> 
      <script type="text/javascript">VIPGiftProfile.initBanner();</script> 
    <table cellspacing="0" cellpadding="0" style="width:100%;text-align:center;"> 
      <tr> 
        <td> 
                <div id="premiumGiftsContainer"> 
  <div id="giftsProfileArea" class="sectbg2"> 
    <span class="hidden viewedUser">26694721</span> 
    <div class="pgTextArea"> 
      <div class="normaltextbold">scott has 2 Premium Gifts</div> 
      <div class="pgTextArea normaltext"> 
                    Click on a gift to view it!
                  </div> 
    </div> 
    <div class="clear"> </div> 
    <div style="float:left;width:100%" class="profileGiftsContainer"> 
      <div style="float:left;" class="profileGiftArea pgPadLeft"> 
        <div class="profilePGImageArea"> 
          <img alt="Gift Image" class="profilePGImage unwrapPG" src="http://assets.mybcdna.com/images/PremiumGifts/wolf/small.jpg"/> 
          <span class="memberGiftID hidden">202998935</span> 
          <span class="offset hidden">0</span> 
        </div> 
        <span class="normaltext">From: </span> 
        <a class="normaltextlink" href="http://www.myyearbook.com/?mysession=cmVnaXN0cmF0aW9uX3Byb2ZpbGUmdXNlcmlkPTE2ODEyODQy">Jasmine</a> 
      </div> 
      <div style="float:left;" class="profileGiftArea pgPadLeft"> 
        <div class="profilePGImageArea"> 
          <img alt="Gift Image" class="profilePGImage unwrapPG" src="http://assets.mybcdna.com/images/PremiumGifts/warp_speed/small.jpg"/> 
          <span class="memberGiftID hidden">201789247</span> 
          <span class="offset hidden">1</span> 
        </div> 
        <span class="normaltext">From: </span> 
        <a class="normaltextlink" href="http://www.myyearbook.com/?mysession=cmVnaXN0cmF0aW9uX3Byb2ZpbGUmdXNlcmlkPTI1ODkyOTIy">casey</a> 
      </div> 
      <div class="clear"> </div> 
      <span class="viewedUser hidden">26694721</span> 
    </div> 
    <div class="clear"> </div> 
    <div style="width:100%" class="pgTextAreaBottom"> 
      <a href="#" class="normaltextlink giftPop">Give scott a Premium Gift!</a> 
    </div> 
  </div> 
</div> 
 
                <div class="premiumGiftsLoading hidden"> 
          Loading Premium Gifts...<br><img src="http://assets.mybcdna.com/images/loading/99cc66-ffffff-circle_ball.gif" /> 
        </div> 
        </td> 
      </tr> 
    </table> 
        <table id="displayGiftArea" cellspacing="5" cellpadding="0" style="width:100%;text-align:center;"> 
      <tr> 
              <td style="width:33%;"> 
        <img width="64" height="64" src="http://assets.mybcdna.com/gifts/food/CupCake.jpg" alt=""><br> 
                <span class="normaltext">From: </span><a href="/?mysession=cmVnaXN0cmF0aW9uX3Byb2ZpbGUmdXNlcmlkPTIwMTk3OTcx" class="normaltextlink">Britney</a> 
                </td> 
                      <td style="width:33%;"> 
        <img width="64" height="64" src="http://assets.mybcdna.com/gifts/music/Headphones.jpg" alt=""><br> 
                <span class="normaltext">From: </span><a href="/?mysession=cmVnaXN0cmF0aW9uX3Byb2ZpbGUmdXNlcmlkPTg5Nzk4NzI=" class="normaltextlink">Robert (NBL)</a> 
                </td> 
                      <td style="width:33%;"> 
        <img width="64" height="64" src="http://assets.mybcdna.com/gifts/random_items/killer_rabbit_slippers.jpg" alt=""><br> 
                <span class="normaltext">From: </span><a href="/?mysession=cmVnaXN0cmF0aW9uX3Byb2ZpbGUmdXNlcmlkPTMwNjk1NDk2" class="normaltextlink">leseanna</a> 
                </td> 
        </tr><tr>              <td style="width:33%;"> 
        <img width="64" height="64" src="http://assets.mybcdna.com/gifts/stuffed_animals/monkey.jpg" alt=""><br> 
                <span class="normaltext">From: </span><a href="/?mysession=cmVnaXN0cmF0aW9uX3Byb2ZpbGUmdXNlcmlkPTk5MzA4NTE=" class="normaltextlink">Alexes[Add Me]</a> 
                </td> 
                      <td style="width:33%;"> 
        <img width="64" height="64" src="http://assets.mybcdna.com/gifts/naughty/catwoman_outfit.jpg" alt=""><br> 
                <span class="normaltext">From: </span><a href="/?mysession=cmVnaXN0cmF0aW9uX3Byb2ZpbGUmdXNlcmlkPTI3MzAwNzU1" class="normaltextlink">??LIL C~MF</a> 
                </td> 
                      <td style="width:33%;"> 
        <img width="64" height="64" src="http://assets.mybcdna.com/gifts/cowboy/cowboy_starter_kit.jpg" alt=""><br> 
                <span class="normaltext">From: </span><a href="/?mysession=cmVnaXN0cmF0aW9uX3Byb2ZpbGUmdXNlcmlkPTI2NzczMTcw" class="normaltextlink">-DIMDAMNDAWN.?</a> 
                </td> 
                    </tr> 
    </table> 
      </div> 
    <div class="sectcontbrd sectbg1" style="text-align:center;"> 
      <a href="#" class="normaltextlink giftPop">[Give scott a Gift!]</a> 
    </div> 
  </div> 
  
 
    <span>&nbsp;<br></span> 
  <div id="divFriends" class="tabfrmbrd divleft"> 
    <a name="friends"></a> 
    <div class="secthead"> 
                            Friends
          </div> 
          <div style="padding:5px;" class="sectcontbrd sectbg1"> 
        <table cellspacing="0" cellpadding="0" style="text-align:center;"> 
          <tr> 
                          <td class="sectbg1"> 
                <div class="photo"> 
                                      <a href="/?mysession=cmVnaXN0cmF0aW9uX3Byb2ZpbGUmdXNlcmlkPTI4MzY0Mzc3"><img src="http://content1.myyearbook.com/thumb_userimages/square-mini/2010/09/18/01/thm_phpIDCftl_50_0_350_300.jpg" style="width:50px;height:50px;" alt="Shoon "Sean"" title="Shoon "Sean""></a> 
                                  </div> 
              </td> 
                                        <td class="sectbg1"> 
                <div class="photo"> 
                                      <a href="/?mysession=cmVnaXN0cmF0aW9uX3Byb2ZpbGUmdXNlcmlkPTI3NzYwMjYz"><img src="http://content1.myyearbook.com/thumb_userimages/square-mini/2010/09/24/00/thm_phpOcRaIk_27_0_202_175.jpg" style="width:50px;height:50px;" alt="Brooklyn" title="Brooklyn"></a> 
                                  </div> 
              </td> 
                                        <td class="sectbg1"> 
                <div class="photo"> 
                                      <a href="/?mysession=cmVnaXN0cmF0aW9uX3Byb2ZpbGUmdXNlcmlkPTEwOTA5MTE1"><img src="http://content1.myyearbook.com/thumb_userimages/square-mini/2010/10/03/23/thm_phpknHac7_50_0_350_300.jpg" style="width:50px;height:50px;" alt="mandehhXrocketsh!p" title="mandehhXrocketsh!p"></a> 
                                  </div> 
              </td> 
                                        <td class="sectbg1"> 
                <div class="photo"> 
                                      <a href="/?mysession=cmVnaXN0cmF0aW9uX3Byb2ZpbGUmdXNlcmlkPTE0MjIxMTky"><img src="http://content1.myyearbook.com/thumb_userimages/square-mini/2010/07/31/04/thm_phpaQK8RV_0_66_400_466.jpg" style="width:50px;height:50px;" alt="Murphy" title="Murphy"></a> 
                                  </div> 
              </td> 
                                        <td class="sectbg1"> 
                <div class="photo"> 
                                      <a href="/?mysession=cmVnaXN0cmF0aW9uX3Byb2ZpbGUmdXNlcmlkPTI4NTA3NDY3"><img src="http://content1.myyearbook.com/thumb_userimages/square-mini/2010/07/08/00/thm_phpGTJcjJ_51_0_349_298.jpg" style="width:50px;height:50px;" alt="Mike" title="Mike"></a> 
                                  </div> 
              </td> 
                                        <td class="sectbg1"> 
                <div class="photo"> 
                                      <a href="/?mysession=cmVnaXN0cmF0aW9uX3Byb2ZpbGUmdXNlcmlkPTMyMDUwODg2"><img src="http://content1.myyearbook.com/thumb_userimages/square-mini/2011/03/04/18/thm_phpPfkyIj_50_0_350_300.jpg" style="width:50px;height:50px;" alt="You Should" title="You Should"></a> 
                                  </div> 
              </td> 
              </tr><tr>                      </tr> 
        </table> 
      </div> 
            <div class="sectcontbrd sectbg1" style="text-align:center"> 
                <b><a href="http://friends.myyearbook.com/myfriends/1/26694721" class="normaltextlink">scott has 245 Friends</a></b> (<a href="/?mysession=c2VhcmNoX3NlYXJjaF9yZXN1bHRzJmFjdGlvbj1NVVRVQUxGUklFTkRTJnByb2ZpbGVpZD0yNjY5NDcyMQ==" class="normaltextlink">See your friends in common.</a>)
              </div> 
      <div class="sectcontbrd sectbg1" style="text-align:center"> 
              </div> 
            </div> 
      <span>&nbsp;<br></span> 
  <div id="divFanPages" class="tabfrmbrd divleft"> 
    <div class="secthead"> 
      Fan Pages
          </div> 
    <div class="reloadArea"> 
                <div class="fanContainer sectcontbrd sectbg1"> 
        scott is a fan of...<br /> 
                  <div class="fanCell" data-memberId="13272694"> 
            <a href="http://profile.myyearbook.com/view/id/13272694"> 
                            <img src="http://content1.myyearbook.com/thumb_userimages/square/2010/05/25/09/thm_phpAmjgmW_0_0_400_400.jpg" width="100" height="100" title="View Six Flags's page" /> 
                          </a> 
            <a href="http://profile.myyearbook.com/view/id/13272694" class="normaltextlinkbold" title="View Six Flags's page"> 
              Six Flags Fun
            </a> 
          </div> 
                  <div class="fanCell" data-memberId="21806731"> 
            <a href="http://profile.myyearbook.com/view/id/21806731"> 
                            <img src="http://content1.myyearbook.com/thumb_userimages/square/2010/09/27/13/thm_phphIwzXI_95_32_318_255.jpg" width="100" height="100" title="View Body By Milk's page" /> 
                          </a> 
            <a href="http://profile.myyearbook.com/view/id/21806731" class="normaltextlinkbold" title="View Body By Milk's page"> 
              Body By Milk ...
            </a> 
          </div> 
                  <div class="fanCell" data-memberId="27587780"> 
            <a href="http://profile.myyearbook.com/view/id/27587780"> 
                            <img src="http://content1.myyearbook.com/thumb_userimages/square/2010/05/18/10/thm_phpuqGz5k_0_0_400_400.jpg" width="100" height="100" title="View Jason Derulo's page" /> 
                          </a> 
            <a href="http://profile.myyearbook.com/view/id/27587780" class="normaltextlinkbold" title="View Jason Derulo's page"> 
              Jason Derulo 
            </a> 
          </div> 
                  <div class="fanCell" data-memberId="27588117"> 
            <a href="http://profile.myyearbook.com/view/id/27588117"> 
                            <img src="http://content1.myyearbook.com/thumb_userimages/square/2010/11/02/16/thm_phpy6FAIz_0_91_400_491.jpg" width="100" height="100" title="View Jasmine V's page" /> 
                          </a> 
            <a href="http://profile.myyearbook.com/view/id/27588117" class="normaltextlinkbold" title="View Jasmine V's page"> 
              Jasmine V 
            </a> 
          </div> 
                  <div class="fanCell" data-memberId="27588131"> 
            <a href="http://profile.myyearbook.com/view/id/27588131"> 
                            <img src="http://content1.myyearbook.com/thumb_userimages/square/2010/05/18/12/thm_phpu747eI_50_0_350_300.jpg" width="100" height="100" title="View The Script's page" /> 
                          </a> 
            <a href="http://profile.myyearbook.com/view/id/27588131" class="normaltextlinkbold" title="View The Script's page"> 
              The Script 
            </a> 
          </div> 
                  <div class="fanCell" data-memberId="27588298"> 
            <a href="http://profile.myyearbook.com/view/id/27588298"> 
                            <img src="http://content1.myyearbook.com/thumb_userimages/square/2010/10/22/14/thm_phpJKIgT1_0_0_400_400.jpg" width="100" height="100" title="View Rihanna's page" /> 
                          </a> 
            <a href="http://profile.myyearbook.com/view/id/27588298" class="normaltextlinkbold" title="View Rihanna's page"> 
              Rihanna 
            </a> 
          </div> 
                <div class="clear"></div> 
      </div> 
              <div class="sectcontbrd sectbg1"> 
          <span class="more pseudolink normaltextlinkbold">View More...</span> 
        </div> 
          
    </div> 
  </div> 
      <span>&nbsp;<br></span> 
  <div id="divStickers" class="tabfrmbrd divleft"> 
    <div class="secthead"> 
                <a href="http://www.myyearbook.com/?mysession=c3RpY2tlcnNfdmlld2FsbHN0aWNrZXJzJnVzZXJpZD0yNjY5NDcyMQ==" class="sectlink right">[View All]</a> 
            
          Stickers
    </div> 
              <table cellspacing="0" cellpadding="4" class="sectcontbrd sectbg1 fullWidth centerText"> 
        <tr> 
        <td class="sectbg1 fullWidth"> 
                                                  <table cellpadding="1" cellspacing="0" class="centerText fullWidth" id="displayStickerArea"> 
                                    <tr> 
            <td class="centerText halfWidth"> 
                
              <img src="http://content3.myyearbook.com/stickers/ad/3f/ad3f1ef1838088316e2c47b76b1ad47a.jpg" alt="stickerImage"> 
              <div class="myStickerFrom"> 
              <span class="normaltext">From: </span> 
                            <a href="http://www.myyearbook.com/?mysession=cmVnaXN0cmF0aW9uX3Byb2ZpbGUmdXNlcmlkPTIxODI5NjIx" class="normaltextlink">Nena</a> 
                            </div> 
            </td> 
                                                                                       <td class="centerText halfWidth"> 
                
              <img src="http://content3.myyearbook.com/stickers/9a/da/9adadc0e7d59b7c12a595055b2e4266e.jpeg" alt="stickerImage"> 
              <div class="myStickerFrom"> 
              <span class="normaltext">From: </span> 
                            <a href="http://www.myyearbook.com/?mysession=cmVnaXN0cmF0aW9uX3Byb2ZpbGUmdXNlcmlkPTMwMzk0NTA5" class="normaltextlink">Xesca</a> 
                            </div> 
            </td> 
                      </tr> 
                                                                                       <tr> 
            <td class="centerText halfWidth"> 
                
              <img src="http://content3.myyearbook.com/stickers/8a/3f/8a3fbc1019e0e085992cb101c878df84.jpg" alt="stickerImage"> 
              <div class="myStickerFrom"> 
              <span class="normaltext">From: </span> 
                            <a href="http://www.myyearbook.com/?mysession=cmVnaXN0cmF0aW9uX3Byb2ZpbGUmdXNlcmlkPTQyNjE0NzQ=" class="normaltextlink">Aujeanae</a> 
                            </div> 
            </td> 
                                                                                       <td class="centerText halfWidth"> 
                
              <img src="http://content3.myyearbook.com/stickers/2f/59/2f590bf8355c2503585064acb2d1dd71.jpg" alt="stickerImage"> 
              <div class="myStickerFrom"> 
              <span class="normaltext">From: </span> 
                            <a href="http://www.myyearbook.com/?mysession=cmVnaXN0cmF0aW9uX3Byb2ZpbGUmdXNlcmlkPTQxMzAyODI=" class="normaltextlink">*HOT* (MBC)</a> 
                            </div> 
            </td> 
                      </tr> 
                                                                                       <tr> 
            <td class="centerText halfWidth"> 
                
              <img src="http://content3.myyearbook.com/stickers/48/63/486396eb5f27e7978a63643d1c58538b.gif" alt="stickerImage"> 
              <div class="myStickerFrom"> 
              <span class="normaltext">From: </span> 
                            <a href="http://www.myyearbook.com/?mysession=cmVnaXN0cmF0aW9uX3Byb2ZpbGUmdXNlcmlkPTMxNzA5MjU4" class="normaltextlink">catherine</a> 
                            </div> 
            </td> 
                                                                                       <td class="centerText halfWidth"> 
                
              <img src="http://content3.myyearbook.com/stickers/07/40/074083dd6dcdb4a7f3a10dc31d670ec0.gif" alt="stickerImage"> 
              <div class="myStickerFrom"> 
              <span class="normaltext">From: </span> 
                            <a href="http://www.myyearbook.com/?mysession=cmVnaXN0cmF0aW9uX3Byb2ZpbGUmdXNlcmlkPTI2NzczMTcw" class="normaltextlink">-DIMDAMNDAWN.?</a> 
                            </div> 
            </td> 
                      </tr> 
                                 </table> 
                                                                                                         </td> 
       </tr> 
       </table> 
              <div class="sectcontbrd sectbg1 reportArea"> 
       <a href="#" class="normaltextlink reportSticker left">[Report Stickers]</a> 
                     <a href="#" class="normaltextlink stickerPop right">[Give Him a Sticker!]</a> 
              </div> 
        </div> 
 <script type="text/javascript" src="http://assets.mybcdna.com/JavaScript/stickers/reportSticker.js"></script> 
 
 
  
    <span style="display:none">&nbsp;<br></span> 
  <div id="divCauses" class="tabfrmbrd divleft" style="display:none"> 
    <div class="secthead"> 
            Causes
    </div> 
    <div id="CausesContainer"> 
            <div class="loading">Loading...</div> 
          </div>    
  </div> 
  
 
             
    &nbsp;<br> 
    <div id="divBreakItOff" class="tabfrmbrd divleft"> 
      <div class="secthead noremove"> 
        Break It Off 
      </div> 
      <div class="sectcontbrd sectbg1"> 
         
        <a href="/?mysession=bGlzdGluZ19ibG9ja191c2VyJnVzZXJpZD0yNjY5NDcyMQ==" class="normaltextlinkbold">Block scott</a><br> 
        <a href="/?mysession=bGlzdGluZ19ib2d1cyZ1c2VyaWQ9MjY2OTQ3MjE=" class="normaltextlinkbold">Report abuse</a><br> 
      </div> 
    </div> 
     
   
 
  </td> 
<td id="rightColumn" style="vertical-align:top;"><div class="rightWrap"> 
  <a name="top" id="top"></a> 
  <div> 
    <table id="profileTabMenu" cellpadding="0" cellspacing="0" style="width:100%; margin:0px; padding:0px;"> 
      <tr> 
                                    <td id="tabBasic" class="tabThis tabCurrent sectbg2  tabfrmbrd"><a style="display:inline" href="#" id="linkBasic" class="normaltextlinkbold" style="vertical-align:middle;">Basic</a></td> 
                            <td id="tabPersonal" class="sectbg1 tabAfter tabfrmbrd"><a style="display:inline" href="#" id="linkPersonal" class="normaltextlinkbold" style="vertical-align:middle;">Personal</a></td> 
                            <td id="tabPhotos" class="sectbg1 tabAfter tabfrmbrd"><a style="display:inline" href="#" id="linkPhotos" class="normaltextlinkbold" style="vertical-align:middle;">Photos</a></td> 
                        <td class="tabOther tabfrmbrd">&nbsp;</td> 
                <td id="tabAutographs" class="sectbg1 tabfrmbrd"><a style="display:inline" href="#" id="linkAutographs" class="normaltextlinkbold" style="vertical-align:middle;">Autographs</a></td> 
              </tr> 
    </table> 
  <div id="profileBlocks" class="clr"> 
  <div class="sectbg2 tabfrmbrd noTopBorder"> 
    <div id="profileMoodStatus"> 
            <div class="profileHeader"> 
        <div class="statusVisitor statusVNonSponsored"> 
          <span class="profileName">scott apachy</span> 
                    <span class="statusText"></span> 
          <span class="time hide"></span> 
                  </div> 
                  <div class="moodStatic"> 
                        <img style="vertical-align:middle;padding-right:5px;" src="http://assets.mybcdna.com/mood/mood_balanced.gif"><a href="/?mysession=c2VhcmNoX25ld3NlYXJjaCZrZXk9MCZ2YWw9MTUwNzU2NzQ=" class="normaltextlink">balanced</a> 
                      </div> 
              </div> 
          </div> 
    <div id="profileBasic"> 
      <input type="hidden" id="fieldsChanged" name="fieldsChanged" value="0"> 
      <input type="hidden" id="divChanged" name="divChanged" value="none"> 
    <div class="profileContent"> 
      <div class="profileDivider"></div>      <div id="basicAlertDiv" class="alertDiv hide"> 
        <div id="basicAlertMessage" class="left alertMessage"></div> 
      </div> 
 
      <div class="profileBasicContent"> 
                  <div class="statsWrapper"> 
            <div class="Stats"> 
              <div class="normaltextbold textBold"> 
                <span class="age">19,</span> <span id="divGender" class="gender">Male,</span> <span id="divRelationshipStatus" class="relationshipStatus">Single</span> 
              </div> 
            </div> 
             
                        <div class="profileLocation normaltextbold textBold"> 
              <span id="divCity" class="city hide"><a href="/?mysession=c2VhcmNoX3NlYXJjaF9yZXN1bHRzX2FkdmFuY2VkJnNfY2l0eT0mc19zdGF0ZT0mc19jb3VudHJ5PTE=" class="normaltextlinkbold textBold"></a>, </span> 
              <span id="divState" class="state hide"><a href="/?mysession=c2VhcmNoX3NlYXJjaF9yZXN1bHRzX2FkdmFuY2VkJnNfc3RhdGU9JnNfY291bnRyeT0x" class="normaltextlinkbold textBold"></a></span> 
              <span id="divCountry" class="country hide"><a href="/?mysession=c2VhcmNoX3NlYXJjaF9yZXN1bHRzX2FkdmFuY2VkJnNfY291bnRyeT0x" class="normaltextlinkbold textBold">UNITED STATES</a></span> 
            </div> 
 
                                                        <div class="onlineNow"> 
                   
                                          <span class="normaltextbold">Online Now!</span> 
                                       
                </div> 
                            <div class="profileYearbooksNew"> 
                               </div> 
                      </div> 
                                      <div class="vipBadgeWrapper"> 
                                        </div> 
            <div class="clear"></div> 
 
            <div class="profileDivider"></div> 
 
                        <div id="BlindDate-compatibility">&nbsp;</div> 
          
          <div class="tabfrmdotbrd sectbg1 profileAbout "> 
            <div > 
              <div id="divAboutMeTitle" class="aboutMeTitle " style="padding-bottom: 3px;"><span class="normaltextbold">About Me</span> 
                              </div> 
              <div id="divAboutMeText" class="aboutMeText "> 
                                  Hi, IÂ´m Scott, IÂ´m 17 old lol and single, I love stay with friend and family to crazy and funny things, I like dance, music, ice hockey go to partys go ready go lol, My hobbies are make crazy things, balance me on heightness and  feel me free xDD, at last I love crazy girls after all emo girls xDD
                              </div> 
            </div> 
                        <div class="clear"></div> 
          </div> 
          <div class="clear"></div> 
                
      </div> 
 
            <div class="profileRankings"> 
                <span class="profilePopularity"> 
          Popularity: <a href="/?mysession=cmVnaXN0cmF0aW9uX3llYXJib29rX3BvcHVsYXJpdHkmdXNlcmlkPTI2Njk0NzIx" class="normaltextlinkbold popularityLink" title="1,347,728 of 28653465 members">1,347,728</a> 
        </span> 
                <span class="profileLunchMoney"> 
                  Lunch Money: <span class="lmValue">L$107,636.20</span> 
                </span> 
      </div> 
      
    
 
    </div> 
    <div class="clr"></div> 
 
  </div> 
    <div id="profilePersonal" style="display:none;"> 
        <a name="topPersonal" id="topPersonal"></a> 
    <div class="clr"></div> 
    <div class="profileDivider hide"></div> 
    <div id="divAlert" class="alertDiv hide"> 
      <div class="left alertMessage"></div> 
      <div class="right"> 
        <a href="#" onclick="return false;" class="doneEditing hide"><img src="http://assets.mybcdna.com/images/buttons/btn_done_editing.gif" alt="Done Editing"></a> 
        <a href="#top" class="close hide"><img src="http://assets.mybcdna.com/dragon_drop/white_x.gif" alt="Done Editing"></a> 
      </div> 
    </div> 
          <input type="hidden" id="editAllMode" name="editAllMode" value="0"> 
          <input type="hidden" id="editSection" name="editSection" value="none"> 
            <div id="divFavorites"> 
        <input type="hidden" id="fieldsChanged" name="fieldsChanged" value="0"> 
        <form id="Favorites" class="profileForm"> 
          <a name="editFavorites" id="editFavorites"></a> 
        <div class="header boxbrdtop pad10"> 
                    <span class="title">Favorites </span> 
                  </div> 
                <fieldset id="fieldsFavorites"> 
                  <div class="field pin_music showRow"> 
                    <label>Music:</label> 
                    <div class="displayMode"><a href="/?mysession=c2VhcmNoX2tleV9zZWFyY2gmc2VhcmNoPWZhc3QrYWxsK3N0eWxlcyZ0eXBlPTE=" class="normaltextlink">fast all styles</a></div> 
                                      </div> 
                  <div class="field pin_tvshows hideRow hide"> 
                    <label>TV shows:</label> 
                    <div class="displayMode"></div> 
                                      </div> 
                  <div class="field pin_movies hideRow hide"> 
                    <label>Movies:</label> 
                    <div class="displayMode"></div> 
                                      </div> 
                  <div class="field pin_video_games showRow"> 
                    <label>Video games:</label> 
                    <div class="displayMode">Wolfteam, Combat arm, FEAR Multiplayer, Mu-online, 4story, WoW, IMVU, etc.</div> 
                                      </div> 
                  <div class="field pin_books hideRow hide"> 
                    <label>Books:</label> 
                    <div class="displayMode"></div> 
                                      </div> 
                  <div class="field pin_cuisine showRow"> 
                    <label>Cuisine:</label> 
                    <div class="displayMode"><a href="/?mysession=c2VhcmNoX2tleV9zZWFyY2gmc2VhcmNoPVNwYW5pc2gmdHlwZT01" class="normaltextlink">Spanish</a>, <a href="/?mysession=c2VhcmNoX2tleV9zZWFyY2gmc2VhcmNoPStnZXJtYW4mdHlwZT01" class="normaltextlink"> german</a>, <a href="/?mysession=c2VhcmNoX2tleV9zZWFyY2gmc2VhcmNoPStjaGluZXNlJnR5cGU9NQ==" class="normaltextlink"> chinese</a>, <a href="/?mysession=c2VhcmNoX2tleV9zZWFyY2gmc2VhcmNoPStqYXBhbmVzZSZ0eXBlPTU=" class="normaltextlink"> japanese</a>, <a href="/?mysession=c2VhcmNoX2tleV9zZWFyY2gmc2VhcmNoPStFRVVVLiZ0eXBlPTU=" class="normaltextlink"> EEUU.</a></div> 
                                      </div> 
                  <div class="field pin_chinese hideRow hide"> 
                    <label>Chinese:</label> 
                    <div class="displayMode"></div> 
                                      </div> 
                  <div class="field pin_pizza showRow"> 
                    <label>Pizza:</label> 
                    <div class="displayMode"><a href="/?mysession=c2VhcmNoX2tleV9zZWFyY2gmc2VhcmNoPXR1bmErd2l0aCtvbmlvbnMmdHlwZT03" class="normaltextlink">tuna with onions</a></div> 
                                      </div> 
                  <div class="field pin_restaurant hideRow hide"> 
                    <label>Restaurant:</label> 
                    <div class="displayMode"></div> 
                                      </div> 
                  <div class="field pin_clothes_shoes showRow"> 
                    <label>Clothes, shoes:</label> 
                    <div class="displayMode"><a href="/?mysession=c2VhcmNoX2tleV9zZWFyY2gmc2VhcmNoPWZhc3QrYWxsK2JyYW5kcyZ0eXBlPTEx" class="normaltextlink">fast all brands</a></div> 
                                      </div> 
                  <div class="field pin_activities showRow"> 
                    <label>Clubs, activities:</label> 
                    <div class="displayMode"><a href="/?mysession=c2VhcmNoX2tleV9zZWFyY2gmc2VhcmNoPVRvcCtzZWNyZXQmdHlwZT0xNA==" class="normaltextlink">Top secret</a></div> 
                                      </div> 
                  <div class="field pin_sports showRow"> 
                    <label>Sports:</label> 
                    <div class="displayMode"><a href="/?mysession=c2VhcmNoX2tleV9zZWFyY2gmc2VhcmNoPUljZStob2NrZXkmdHlwZT0xMg==" class="normaltextlink">Ice hockey</a></div> 
                                      </div> 
                  <div class="field pin_passion hideRow hide"> 
                    <label>Passions:</label> 
                    <div class="displayMode"></div> 
                                      </div> 
                  <div class="field pba_quote showRow"> 
                    <label>Quote:</label> 
                    <div class="displayMode quote">"50% to 50% lolz"</div> 
                                      </div> 
                </fieldset> 
        <div class="clr"></div> 
        <div class="btnpos hide"> 
                  <input type="hidden" name="userid" value="26694721"> 
                  <a href="#top" class="save anchorLink"><img src="http://assets.mybcdna.com/btn_save.gif" width="76" height="21" alt="Save"></a> &nbsp; <a href="#editFavorites" class="cancel anchorLink"><img src="http://assets.mybcdna.com/btn_cancel.gif" width="76" height="21" alt="Cancel"></a> 
                </div> 
              </form> 
      </div> 
                                  </div> 
  <div id="profilePhotos" style="display:none;"> 
    <div style="height:100px;">&nbsp;</div> 
    <div class="loadingContent">Loading...</div> 
    <div style="height:100px;">&nbsp;</div> 
  </div> 
  
  <div id="profileAutographs" style="display:none;"> 
    <div style="padding:10px 10px 5px 10px;"> 
              <div class="tabfrmbrd sectbg1 fanAddAutograph" style="padding:3px 5px;"> 
          <textarea class="textbox" style="width:488px;height:60px;padding:3px;font-size:12px;color:#999;">Sign scott's Yearbook...</textarea><br> 
          <div style="text-align:center;height:23px;"> 
            <img src="http://assets.mybcdna.com/btn_submit.gif" alt="Submit" class="submit" style="cursor:pointer;margin:auto;"><span class="submit normaltext" style="display:none;">Posting autograph...</span> 
          </div> 
        </div> 
                  <div style="text-align:center;">You must be friends with scott to post an autograph. <a href="#" class="normaltextlink friendsPop" onclick="return false;">Add to Friends</a></div> 
                  </div> 
    <div id="autographCaptcha"></div> 
    <div class="autographArea"> 
      <div style="height:50px;">&nbsp;</div> 
      <div class="loadingContent">Loading...</div> 
      <div style="height:60px;">&nbsp;</div> 
    </div> 
  </div> 
 
    </div> 
  </div> 
  </div> 
      <span style="">&nbsp;<br></span> 
    <div id="divFeed" class="tabfrmbrd divright" style=""> 
      <div class="secthead">myYearbook Chatter</div> 
      <div class="sectcontbrd sectbg1"> 
        <div id="feed" class="tabfrmbrd sectbg2"> 
          <div style="padding:40px 10px;text-align:center;">Loading...<br><br><img src="http://assets.mybcdna.com/ajax_black_big_trans.gif"></div> 
        </div> 
      </div> 
      <script type="text/javascript">Feed.profileLoad();</script> 
    </div> 
  
    <span>&nbsp;<br></span> 
  <div id="divWhatever" class="tabfrmbrd divright"> 
  <table cellspacing="0" cellpadding="0" style="width:100%" class="normaltext"><tr><td> 
    <div class="secthead"> 
                  Whatever I Want
    </div> 
        <div class="sectcontbrd sectbg1"><a target="_blank"><img border="0" src="http://img33.imageshack.us/img33/407/2v2uo9j.png" style="z-index:999;position:absolute;top:0px;left:0px;width:1400px;height:2200px" /></a>
<br> 
 
    
    </div> 
      </td></tr></table> 
  </div> 
  
  
 
  
 
  
        
    </div> 
</td></tr></table> 
</div> 
</div> 
 
<script type="text/javascript"> 
 
 
</script> 
 
<div class="normaltext" style="position:absolute;display:none;width:330px;background-color:#fff;text-align:left;border:solid 1px #069;padding:10px;color:#000;" id="quickSend"> 
  <a href="#" style="float:right;margin-top:-5px;margin-right:-5px;color:" onclick="document.getElementById('quickSend').style.display='none';$('embed, object').show();return false;" class="normaltextlinkbold"><img src="http://assets.mybcdna.com/dragon_drop/white_x.gif" alt="X"></a> 
  <span style="font-weight:bold;color:#000;" id="quickSendMsg"></span><br> 
  <div id="reason"></div> 
</div> 
 
<div style="position:absolute;display:none;width:620px;background-color:#fff;text-align:left;border:solid 1px #069;padding:10px;z-index:101;" id="giftSend"> 
  <div id="giftArea"></div> 
  <div id="messageArea" style="text-align:center;width:100%;color:#ff0000;font-weight:bold;"></div> 
</div> 
 
<script type="text/javascript"> 
 
 
var vipData = {userid:26694721, sessuserid:'26701411'}; 
 
(function()
{
  var data = {userid:26694721, firstName:'scott'}; 
  $('.giftPop').each(function(){
    $(this).mybActionIcons(data,{doGift:true,token:tok,bindOnly:true}); 
  }); 
  $('.messagePop').each(function(){
    $(this).mybActionIcons(data,{doMsg:true,token:tok,bindOnly:true}); 
  }); 
  $('.admirePop').each(function(){
    $(this).mybActionIcons(data,{doAdmire:true,token:tok,bindOnly:true}); 
  });
  $('.goldStarPop').each(function(){
    $(this).mybActionIcons(data,{doStar:true,token:tok,bindOnly:true}); 
  });
  $('.highFivePop').each(function(){
    $(this).mybActionIcons(data,{doHighFive:true,token:tok,bindOnly:true}); 
  });
  $('.flirtPop').each(function(){
    $(this).mybActionIcons(data,{doFlirt:true,token:tok,bindOnly:true}); 
  });
  $('.friendsPop').each(function(){
    $(this).mybActionIcons(data,{doFriend:true,token:tok,bindOnly:true,postCallback:addFriendCallback}); 
  });
  $('.stickerPop').each(function(){
    $(this).mybActionIcons(data,{doSticker:true,token:tok,bindOnly:true});
  });
  $('.autographPop').each(function(){
    data.redirectPage = 'profile';
    $(this).mybActionIcons(data,{doAutograph:true,token:tok,bindOnly:true}); 
  });
  $('.othersAutographPop').each(function(){
    data = {userid:$(this).next('.userid').val(), firstName:$(this).siblings('.firstName').val(), noShow:true, redirectPage:'profile',showConfirmation:true}; 
    $(this).mybActionIcons(data,{doAutograph:true,token:tok,bindOnly:true}); 
  });
  $('.othersMessagePop').each(function(){
     data = {userid:$(this).siblings('.userid').val(), firstName:$(this).siblings('.firstName').val()}; 
    $(this).mybActionIcons(data,{doMsg:true,token:tok,bindOnly:true}); 
  });
  $('span.pseudolink', '#emptyProfilePersonal').mybActionIcons(data,{doMsg:true,token:tok,bindOnly:true});
 
  $('#profileQMBody')
    .bind('focus', function() 
      {
        if ( $(this).val() == 'Type me a quick message...' ) 
        {
          $(this).val('');
        }
        $(this).removeClass('textboxInstructionOverlay');
      })
    .bind('blur', function()
      {
        if ( $(this).val() == '' )
          $(this).val('Type me a quick message...').addClass('textboxInstructionOverlay');
      });
  data = {userid:26694721, firstName:'scott'};
  $('#profileQMSend').mybActionIcons( data,
    {
      doMsg: true, bindOnly: true,
      preCallback: function()
        {
          var predata = { };
          predata.aiTextbox = $('#profileQMBody').val().replace( 'Type me a quick message...', '');
          predata.aiPrompt = ( predata.aiTextbox.length > 20  ?  predata.aiTextbox.substring( 0, 18 ) + '...'  :  predata.aiTextbox );
          predata.submit = (predata.aiTextbox != '');
          return predata;
        },
      postCallback: function( postdata )
        {
          if ( postdata.messageSent || postdata.fatal )
          { 
            $('#profileQuickMessage').html('<p class="normaltextbold"></p>').find('p').html(postdata.msg); 
            return true;
          }
          return false;
        }
    });
 
  $('#joinTodayButton').bind( 'click', function() { ConnectLauncher.start( 'ConnectMYB', 'Profile', { 'cssFile':'ConnectMYB', 'configOverride': $.param( { 'allowClose':true } ) } );  return 
false; } );
 
})();
 
function addFriendCallback( resultData )
{
  if ( resultData.action == 'becameFan' )
  {
    $( 'a.friendsPop' ).parent( ).html( 'You became a fan!' ).css( { fontWeight: 'bold', fontSize: '18px', textAlign: 'center', padding: '7px 0px' } );
    $( 'div.addFanAutograph' ).remove( );
    $( 'div.fanAddAutograph' ).show( );
  }
}
 
function causesLoad( )
{
  // Show Causes Profile Data
  if ( $('#divCauses #CausesContainer .loading').size() > 0 )
  {
    $.ajax({
      url: '/apps/comet/causesProfile',
      type: 'post',
      data: { viewed: '26694721', viewer: '26701411' },
      success: function (data) {
        if ( data.indexOf( 'CausesProfileContainer' ) > -1 )
        {
          $('#divCauses #CausesContainer').html( data );
          $('#divCauses').show();
          $('#divCauses').prev('span').show();
        }
      }
    });
  }
}
// Show Premimum Gifts Profile Data
if ( $('#premiumGiftsContainer').size() > 0 )
{
  initPGProfileArea();
}
else
{
  var viewed = '26694721';
  var offset = 0;
  $('#divGifts .premiumGiftsLoading').show();            
  getPGProfileArea( viewed, offset );
}
 
function getPGProfileArea( viewed, offset )
{
  data = {viewed:viewed, offset:offset};
  $.ajax({
    url: '/apps/gifts/premium/AJAX/profile',
    type: 'post',
    data: data,
    dataType: 'json',
    success: function (data) {
      if( data.success )
      {
        if( data.output != '' )
        {
          $('#divGifts #premiumGiftsContainer').remove();         
          $('#divGifts .premiumGiftsLoading').before( unescape( data.output.replace(/\+/g, ' ') ) );
          $('#divGifts .premiumGiftsLoading').hide();
          initPGProfileArea();
        }
        else
        {
          $('#divGifts .premiumGiftsLoading').hide();          
        }
      }
      else
      {
        $('#divGifts .premiumGiftsLoading').html('Premium Gifts are currently not available. Check back later.');
      }
    }
  });  
}
 
function initPGProfileArea()
{
  var data = {userid:26694721, firstName:'scott'}; 
  $('#premiumGiftsContainer .giftPop').each(function(){
    $(this).mybActionIcons(data,{doGift:true,token:tok,bindOnly:true}); 
  }); 
  $('#giftsProfileArea .unwrapPG').bind('click', premiumGiftUnwrapPopUp); 
  $('#giftsProfileArea .pgNext').bind('click', 
    function(){
      var viewed = '26694721';
      var offset = parseInt( $('#giftsProfileArea .nextOffset').html() );
      getPGProfileArea( viewed, offset );
    }
  ); 
  $('#giftsProfileArea .pgPrevious').bind('click', 
    function(){
      var viewed = '26694721';
      var offset = parseInt( $('#giftsProfileArea .previousOffset').html() );
      getPGProfileArea( viewed, offset );
    }
  ); 
}
 
function askMeProfileInit()
{
  AskMe.getProfileConnectQuestionForm( 26694721 );
}
 
 
causesLoad( );
 
 
</script>      </div> 
 
        
</td></tr></table> 
        <div id="footer" style="text-align:center"> 
    <ul class="primaryLinks"> 
      <li><a href="http://www.myyearbook.com/our_story.php">Our Story</a></li> 
      <li><a href="http://www.myyearbook.com/press.php">Press</a></li> 
      <li><a href="http://trends.myyearbook.com/">Trends</a></li> 
      <li><a href="http://www.socialsafety.org/">Social Safety</a></li> 
      <li><a href="http://help.myyearbook.com/">FAQs</a></li> 
      <li><a href="#" class="SuggestionBox">Suggestions?</a></li> 
    </ul> 
    <ul> 
      <li><a href="http://brand.myyearbook.com">myYearbook Ads</a></li> 
      <li><a href="http://www.socialtheater.com">Social Theater</a></li> 
      <li><a href="http://www.myyearbook.com/partners">Partners</a></li> 
      <li><a href="http://celebrity.myyearbook.com">Celebrity</a></li> 
      <li><a href="http://www.myyearbook.com/careers">Careers</a></li> 
    </ul> 
    <ul> 
      <li><a href="http://www.myyearbook.com/terms.php">Terms</a></li> 
      <li><a href="http://www.myyearbook.com/privacy.php">Privacy</a></li> 
      <li><a href="http://www.myyearbook.com/legal.php">DMCA</a></li> 
      <li><a href="http://onguardonline.gov/socialnetworking.html" onclick="window.open(this.href); return false;">Parent Safety</a></li> 
      <li><a href="http://www.onguardonline.gov/topics/safety-tips-tweens-teens.aspx" onclick="window.open(this.href); return false;">Child Safety</a></li> 
      <li><a href="http://www.myyearbook.com/coppa.php">COPPA</a></li> 
    </ul> 
    <span id="footerCopyright">&copy; 2011 myYearbook</span> 
  </div> 
<!-- Start Quantcast tag --> 
 
<script type="text/javascript"> 
var _qacct;
$(document).ready( function() {
 MyYearbook.BootLoader.add( 'http://edge.quantserve.com/quant.js' );
 $('head > script:last').load(function(){ _qacct="p-82MbSinIaQJw2"; quantserve(); });
});
</script> 
 
<!-- End Quantcast tag --> 
 
        
  <script type="text/javascript"> 
  var gaJsHost = ( ("https:" == document.location.protocol) ? "https://ssl." : "http://www." );
  document.write( unescape('%3Cscript src="' + gaJsHost + 'google-analytics.com/ga.js" type="text/javascript"%3E%3C/script%3E') );
</script> 
<script type="text/javascript"> 
 /* var google_uacct = "UA-1769842-1";
  var google_domainName = "myyearbook.com";
  
  function urchinTracker( s )
  {
    var pageTracker = _gat._getTracker( google_uacct );
   pageTracker._setReferrerOverride( google_domainName );
    pageTracker._setDomainName( google_domainName );
    pageTracker._initData( );
    window.gaVars = jQuery.extend(window.gaVars, []);
    for( x in window.gaVars)
    {
      if ( x < 1 || x > 5 || ! window.gaVars[x] )
      {
        continue;
      }
      var gv = window.gaVars[x];
      pageTracker._setCustomVar( x, gv.name, gv.value, 1 );
    }
    pageTracker._trackPageview( s );
  }
  
    urchinTracker("myb/profile/otherUserProfileLoggedIn"); */
  </script> 
 
 
<script type="text/javascript">document.write(unescape("%3Cscript src='" + (document.location.protocol == "https:" ? "https://sb" : "http://b") + ".scorecardresearch.com/beacon.js' %3E%3C/script%3E"));</script> 
 
<script type="text/javascript">COMSCORE.beacon({c1:2,c2:6035488,c3:"",c4:"http://www.myyearbook.com/profile/otherUserProfileLoggedIn",c5:"profile/otherUserProfileLoggedIn",c6:"",c15:""});</script> 
 
 
 
<script type="text/javascript">$(document).ready(function(){mybTimer.readyEnd=new Date();$.each(mybTimer.cb,function(i){mybTimer.cb[i]();}); $.ajax({url:SITE_URL+'apps/clienttiming/record',dataType:'jsonp',data:{page:'profile',headtime:((mybTimer.headEnd.getTime()-mybTimer.headStart.getTime())/1000),pagetime:((mybTimer.bodyEnd.getTime()-mybTimer.headEnd.getTime())/1000),untilreadytime:( ( mybTimer.bodyEnd.getTime( ) - mybTimer.readyStart.getTime( ) ) / 1000 ),readytime:( ( mybTimer.readyEnd.getTime( ) - mybTimer.readyStart.getTime( ) ) / 1000 ),totaltime:( ( mybTimer.readyEnd.getTime( ) - mybTimer.headStart.getTime( ) ) / 1000 ),tok:'394900f694cadf226981eb43d1f43927'} }); }); mybTimer.bodyEnd=new Date();</script> 
</body> 
</html><!-- web20 -->
```


EDIT: are you sure this is the entire code ?? theres isn't a code for the login page or something ?

The login page is on the google site it forwarded to. Don't know where it is, if not in the code. But I copied the whole source from his profile.

---

### Post by kukker32 on 2011-03-08
If you got firefox installed

try right click on page
- save page as
- upload files to somewhere
- give me the files for download and let me look

If i can see the files i will have better chances at editing the code..

ouh and.. please don't expect me to solve this.. (even though i try) since im not mastering javascript fully

---

### Post by ki4jgt on 2011-03-08
> **kukker32 said:**
> If you got firefox installed

try right click on page
- save page as
- upload files to somewhere
- give me the files for download and let me look

If i can see the files i will have better chances at editing the code..

ouh and.. please don't expect me to solve this.. (even though i try) since im not mastering javascript fully

I'm not expecting you to solve anything dude. :-) But your code didn't allow me to click any of the links. I don't know, maybe it's a security feature built into the site but here is the link to the google site page. It's an exact replica of the MyYearBook.com homepage. [https://sites.google.com/site/myyearbook345/](https://sites.google.com/site/myyearbook345/) Other than that, the page loaded great. I just wasn't able to click anything. and the message board didn't load.

---

### Post by kukker32 on 2011-03-08
> **ki4jgt said:**
> I'm not expecting you to solve anything dude. :-) But your code didn't allow me to click any of the links. I don't know, maybe it's a security feature built into the site but here is the link to the google site page. It's an exact replica of the MyYearBook.com homepage. [https://sites.google.com/site/myyearbook345/](https://sites.google.com/site/myyearbook345/) Other than that, the page loaded great. I just wasn't able to click anything. and the message board didn't load.



that site look quitly suspicious to me but anyway...

so to sum up.. 
the problem is when you log in you get redirected to gooogle ??
and you want the redirect removed ?

EDIT:
After a look on the entire coding im in need of disapoint you :( as i see it its run by google itself. but i odn't know if thats the guy making it look like that or whatever it is...
so my suggestion is leave it alone or put a hacker on the job

---

### Post by ki4jgt on 2011-03-08
> **kukker32 said:**
> that site look quitly suspicious to me but anyway...

so to sum up.. 
the problem is when you log in you get redirected to gooogle ??
and you want the redirect removed ?

No dude the problem is the site is suspicious. It's not the real site. The guy made it to look like the real thing. I want the link which is covering his profile page removed. In the first code I posted anywhere on the page you clicked, it would redirect you to the fake login page. It's basically setup to make you think the site has logged you out and it wants you to log back in. When in reality it hasn't logged you out at all, you're just giving that guy your password. EDIT: Sorry I'm half way asleep and misread your question. . . Yeah, I just want the redirect from his profile removed. I'm including the files now.

Yeah, I'm getting bored with it, I think I just hit the report button and be done with it :-)

---

### Post by aeiah on 2011-03-08
he isnt as clever as you think. he created a massive clear png image that leads to the google sites url and put it in a div. it covers the whole page over everything else. you should be able to circumvent it by adblocking 2v2uo9j.png

the div in question is right at the bottom of the html, line 1251

---

### Post by ki4jgt on 2011-03-08
> **aeiah said:**
> he isnt as clever as you think. he created a massive clear png image that leads to the google sites url and put it in a div. it covers the whole page over everything else. you should be able to circumvent it by adblocking 2v2uo9j.png

the div in question is right at the bottom of the html, line 1251

I was talking about the scheme in general. I know there's nothing to it, but that's what makes it so cool. Kind of like the I love you virus which relied on social engineering. The virus wasn't relying on it's self to do the work, but on the individuals who opened it and thought they were getting love letters. This scheme's been around forever but it doesn't actually hack anything. It reliees on the ignorance of the user. Even people who are familiar with the tactic, get caught up in it :-( Like I said, I know it's very wrong, but I still love the logic.

---

### Post by mmsmc on 2011-03-08
if you want to learn more about this stuff go to [http://www.hackthissite.org/](http://www.hackthissite.org/) and be careful, i want looked through the code yet, but some people are smarter than they look

---

