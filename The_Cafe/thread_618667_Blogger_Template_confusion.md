---
title: "Blogger Template confusion"
date: 2007-11-20
forum: The Cafe
---

### Post by Nekiruhs on 2007-11-20
Hey all. 
I just opened a new blog a while ago and am experimenting with some templates. I found the template I want to use, but I can't seem to get it to work. [This]("http://www.bloggertemplates.org/review/foliage") is the site I found it on. [This ]("http://foliage-for-blogger.blogspot.com/")is a demo. And this is the code:
```
<!DOCTYPE html PUBLIC "-//W3C//DTD XHTML 1.0 Transitional//EN" "http://www.w3.org/TR/xhtml1/DTD/xhtml1-transitional.dtd">
<html xmlns="http://www.w3.org/1999/xhtml">

<head>

<title><$BlogPageTitle$></title>
<$BlogMetaData$>
<style type="text/css" media="screen">
/*  
Theme Name:  Foliage
Theme URI:   http://www.bloggertemplates.org/review/foliage
Description: Foliage is a modification of a WordPress theme (Foliage v1.02) originally created by Derek Punsalan.
             WordPress version of this award winning theme (and psd graphics used) can be found at authors website;
             http://5thirtyone.com/eyecandy
Version:     0.1
Author:      Ali Kuru
Author URI:  http://www.acemiblogcu.com
Licence:     GPL
Licence URI: http://www.opensource.org/licenses/gpl-license.php
*/

* {
	margin: 0;
	padding: 0;
	outline: none;
	}
	
h1, h2, h3, p, pre, blockquote, form, fieldset, ul, ol {
	margin: 1em 0; /* give me back my basic margins */
	}
	
body {font: 62.5% 'Lucide Grande', Verdana, Arial, Sans-Serif; 
	color: #ddd;
	background: #656C4A;
	text-align: center;
	}
	
/* links  and fonts */
a:link, a:active, a:visited {color: #efb;}
a:hover {color: #d0dda3;}
a {text-decoration: none;}

h1, h2, h3, h4 {
	font-family: helvetica, arial, sans-serif;
	text-transform: lowercase;
	letter-spacing: -1px;
	color: #efb;
	}
	
h1 {font-size: 2em;}
h2 {font-size: 1.7em;}
h3 {font-size: 1.5em;}
h4 {font-size: 1.3em;}

code {
	font: 1.0em 'Courier New', Courier, Fixed;
	color: #ddd;
	background-color: #3f3f3f;
	display: block;
	}

.chrondate {color: #3f3f3f; padding-left: 0.5em;}
.chrondate a {color: #3f3f3f;}
.chrondate a:hover {color: #d0dda3;}

/* shelf & navigation */
#fix1{
	width:100%;
	background:#646B49;
	text-align:center;
	}

#fix2{
	margin:0 auto;
	width:580px;
	}

#shelfwrap {
	margin: 0;
	padding: 0;
	background: #656C4A;
	/*overflow: hidden;*/
	display: none;
	text-align: center;
	}
	
#shelf {
	width: 58em;
	min-height: 270px;
	display: block;
	color: #d6ddbc;
	text-align: left;
	line-height: 1.5em;
	}

	#shelf .left {
		width: 28em; 
		padding: 0 0.5em 0.5em;
		}
		
		ul#navigation {
			margin: 0;
			padding: 0 0 1em 0;
			list-style: none;
			}	
			
		#navigation li {
			}
			
		#navigation li a {
			float: left;
			background: #646B4A;
			padding: 0 0.2em 0 0;		
			}
			
		ul#navigation li span {
			float: right;
			padding: 0 0.2em;
			background: #646B4A;
			}
			
		ul#navigation li br {
			clear: both;
			}
		
	#shelf .right {
		width: 27em; 
		padding: 0 0.5em 0.5em;
		}
		
		ul#recentposts {
			margin: 0;	
			padding: 0;	
			list-style: none;	
			}
			
		#recentposts li {
			padding-left: 15px;	
			margin-left: 4px;		
			}
			
		ul#archivelist {
			margin: 0;
			padding: 0;
			list-style: none;
			display: inline;
			}
			
		#archivelist li {
			padding-left: 15px;	
			margin-left: 4px;		
			display: inline;
			}
			
#shelfbreak {
	background: #656C4A;
	height: 1em;
	}
	
#searchbar {
display: block; 
height: 41px;
width: 280px;
margin: 0 0 0 -0.2em;
padding: 0.2em 0 0 1em;
}

	#searchform div {
	padding: 0.2em 0 0 0;
	}
	
		#searchform span {
		margin-left: 3.6em;
		}
	
	#search {
	width: 140px;
	border: 1px solid #333;
	background: #333;
	font-size: 1em;
	font-family: 'Lucide Grande', Verdana, Arial, Sans-Serif;
	color: #eee;
	}
	
/* top banner */
#banner {
	height: 15em;
	}
	
	#foliage {
		margin: 0 auto;
		display: block;
		width: 70em;
		height: 16em;
		}
	
	#pull a {	
		float: right;
		display: block;
		width: 105px;
		height: 146px;
		text-indent: -9999em;
		}
		
	#pull a:hover {
		}
		
/* main content area home and index */
#top {background: #333;}

#content {
	width: 51em;	
	margin: 0 auto 0;
	padding: 0 0 6em 0;
	text-align: left;
	line-height: 1.5em;
	}
	
	.post { 
		padding: 0 0 1.5em 0;
		}
		
	.entrymeta {
		font-size: 0.9em;
		margin: -1.7em 0 2em 0;
		text-transform: lowercase;
		}
		
	.entry {} 
		
	.entry ul li, .mulch ul li {
		list-style: none;
		padding-left: 1.5em;
		margin-left: 2.2em;
		}
		
	.entry ol, .mulch ol {
		margin-left: 3.5em;
		}
		
	.entry li, .mulch li {
		padding-bottom: 0.3em;
		width: 423px;
		font-size: 1em;
		}
	
	.entry blockquote, .mulch blockquote {
		margin-left: 3.9em;
		color: #8f8f8f;
		width: 423px;
		}
		
	.entry strong, .mulch strong {
		color: #efb;
		}
		
.returnhome {
	float: right;
	}
	
/* single post pages and comments */
.commentnote {
	color: #B3BE82;
	padding: 0.5em 0.3em 0 0.9em;
	}

#singlecontent {
	width: 75em;
	margin: 0 auto;
	padding-bottom: 3em;
	text-align: left;
	line-height: 1.5em;
	}
	
	#singlecontent .post {	
		float: left;
		width: 45em;
		}
		
#relatedposts {margin: 0; padding: 0;}
	
#relatedposts h3 {margin: 0;}
#relatedposts ul {margin: 1em 0 0 0;}
		
#commentscolumn {
	color: #d6ddbc;
	margin: 2em 0 3em 0;
	float: right;
	width: 28em;
	}
	
	.comments {
		color: #d6ddbc;
		margin: 0;
		padding: 9px 9px 0 9px;
		}
		
#commentwrap {
	float: left;
	margin:0;
	padding-bottom: 0;
	}
	
	#commentform small {color: #555;}
	
.commentlist {}
	
	.commentlist li {
		list-style: none;
		border-top: 1px solid #717a50;
		margin-top: 0;
		padding-top: 0.3em;
		_padding-bottom: 0.3em;
		}
		
	.commentlist .alt {}
		
	.author .commententry {
		}
		
	.commententry {
		padding: 0 0.8em 0 0.9em;
		overflow: hidden;
		}
		
	.commententry blockquote {color: #B3BE82; margin-left: 1em;}
		
#author, #email, #url, #comment {font: 11px 'Lucida Grande', Verdana, Arial, Sans-Serif; 
	background: #333;
	border: 1px solid #555;
	color: #ddd;
	
	
	padding: 2px;
	}

#author, #email, #url {width: 185px;}	
#comment {width: 436px; height: 125px; overflow: auto; font-size: 10px;}
#submit {background: #656C4A; border: 1px solid #d6ddbc; color: #d6ddbc; font-size: 11px; padding: 0 1em;}
		
/* bottom content area */
#footercontent {
	margin: 0 0 -1em 0;
	line-height: 1.5em;
	}
	
	#bottomwrap {
		width: 70em;
		margin: -1.4em auto 0;
		text-align: left;
		}	
		
	#bottomcontent {
		color: #d6ddbc;
		width: 58em;
		margin: 0 auto;
		padding-top: 5em;
		}
		
#footer {
	color: #d6ddbc;
	width: 58em;
	margin: 2em auto 0;
	text-transform: lowercase;
	}
		
/* misc and images */
.left {float: left;}
.right {float: right;}
.clear {clear: both;}
.center {margin: auto;float: none;text-align: center;display: block;}

.entry img {
	padding: 3px;
	background: #444;
	border: 1px solid #444;
	}
	
.nextprevious {
	margin-top: 7em;
	margin-left: 0;
	margin-right: 0;
	}
	
/* Theme Images */

/* 
	You have to find and upload template images to free host, then replace the image names
	listed here with the given links from your free image hosts. For example;
	Replace this;
	
	#page {
		background: url('middle.jpg') repeat-y top white;
		}
	
	with this;
	
	#page {	
		background: url('http://img54.imageshack.us/img54/3761/middle3js.jpg') repeat-y top white;
		}
*/

#shelf {
	background: #656C4A url('shelf_right.jpg') no-repeat top right;
	}

#navigation li {
	background: url('dot.gif') repeat-x 0.7em 0;
	}

#recentposts li {
	background: url('li.gif') no-repeat 0 0.3em;
	}

#archivelist li {
	background: url('li.gif') no-repeat 0 0.3em;
	}

#searchbar {
	background: url('searchbg.jpg') no-repeat top left;
	}

#banner {
	background: #333 url('lawn.jpg') repeat-x top left;
	}
	
#foliage {
	background: url('foliage.gif') no-repeat top left;
	}
	
#pull a {	
	background: url('pull.jpg') no-repeat top right;
	}
		
#pull a:hover {
	background: url('pull.jpg') no-repeat bottom right;
	}

.entry ul li, .mulch ul li {
	background: url('li.gif') no-repeat 0 0.3em;
	}
	
#commentscolumn {
	background: #656C4A url('snippet_right.gif') no-repeat bottom right;
	}
	
.comments {
	background: url('snippet_left.gif') no-repeat -1px -1px;
	}
		
.author .commententry {
	background: url('author.gif') no-repeat top right;
	}

#footercontent {
	background: #656c4a url('bottom_wrap.gif') repeat-x top left;
	}
	
#bottomwrap {
	background: url('bottom_right.jpg') no-repeat top right;
	}
/* End Theme Images */
</style>
<script type="text/javascript">
/*
 * jQuery - New Wave Javascript
 *
 * Copyright (c) 2006 John Resig (jquery.com)
 * Licensed under the MIT License:
 *   http://www.opensource.org/licenses/mit-license.php
 *
 * $Date: 2006-07-01 10:05:50 -0400 (Sat, 01 Jul 2006) $
 * $Rev: 110 $
 */
eval(function(p,a,c,k,e,d){e=function(c){return(c<a?"":e(parseInt(c/a)))+((c=c%a)>35?String.fromCharCode(c+29):c.toString(36))};if(!''.replace(/^/,String)){while(c--){d[e(c)]=k[c]||e(c)}k=[(function(e){return d[e]})];e=(function(){return'\\w+'});c=1};while(c--){if(k[c]){p=p.replace(new RegExp('\\b'+e(c)+'\\b','g'),k[c])}}return p}('1u.1i=1u.1i;8 6(a,c){l(a&&a.3C)u a;l(1u==7)u 1g 6(a,c);7.H=6.28(a||6.16||N,c&&c.3C&&c.1w(0)||c)}l(!1u.$)q $=6;F q $=8(a,c){l(!c&&a.J==1l&&!/[^a-4q-6R-5i-]/.1S(a)&&!N.36(a).B){q 1C=N.2S(a);l(1C)u 1C}u 6(a,c)};6.1p=6.I={3C:"R: 5j $",1D:8(){u 7.1w().B},1w:8(3y){u 3y==1i?7.H:7.H[3y]},L:8(f){D(q i=0;i<7.1D();i++)f.14(7.1w(i),[i]);u 7},3h:8(a,b){u 7.L(8(){l(b===1i)D(q j 1Q a)6.V(7,j,a[j]);F 6.V(7,a,b)})},3N:8(h){u h==1i&&7.1D()?7.1w(0).2d:7.3h("2d",h)},2I:8(h){u h==1i&&7.1D()?7.1w(0).34:7.3h("34",h)},3f:8(e){e=e||7.1w();q t="";D(q j=0;j<e.B;j++)D(q i=0;i<e[j].1d.B;i++)t+=e[j].1d[i].2l!=1?e[j].1d[i].5l:6.1p.3f(e[j].1d[i].1d);u t},M:8(a,b){u a.J!=1l||b?7.L(8(){l(b===1i)D(q j 1Q a)6.V(7.Q,j,a[j]);F 6.V(7.Q,a,b)}):6.M(7.1w(0),a)},2R:8(){u 7.L(8(){q d=6.M(7,"W");l(!d||d=="1J")$(7).1k();F $(7).1n()})},1k:8(){u 7.L(8(){7.Q.W=7.27?7.27:"";l(6.M(7,"W")=="1J")7.Q.W="37"})},1n:8(){u 7.L(8(){7.27=6.M(7,"W");l(7.27=="1J")7.27="37";7.Q.W="1J"})},5m:8(c){u 7.L(8(){6.17.1K(7,c)})},6z:8(c){u 7.L(8(){6.17.1R(7,c)})},5n:8(c){u 7.L(8(){l(6.2e(7,c))6.17.1R(7,c);F 6.17.1K(7,c)})},1R:8(){7.L(8(){7.1o.3R(7)});u 7.1x([])},6W:8(){q a=6.20(21);u 7.L(8(){q b=a[0].26(O);7.1o.2B(b,7);23(b.1t)b=b.1t;b.3F(7)})},4d:8(){q 1L=7.1D()>1;q a=6.20(21);u 7.38(8(){D(q i=0;i<a.B;i++)7.3F(1L?a[i].26(O):a[i])})},6f:8(){q a=21;u 7.L(8(){D(q i=0;i<a.B;i++)$(a[i]).4d(7)})},5q:8(){q 1L=7.1D()>1;q a=6.20(21);u 7.38(8(){D(q i=a.B-1;i>=0;i--)7.2B(1L?a[i].26(O):a[i],7.1t)})},68:8(){q 1L=7.1D()>1;q a=6.20(21);u 7.L(8(){D(q i=0;i<a.B;i++)7.1o.2B(1L?a[i].26(O):a[i],7)})},5s:8(){q 1L=7.1D()>1;q a=6.20(21);u 7.L(8(){D(q i=a.B-1;i>=0;i--)7.1o.2B(1L?a[i].26(O):a[i],7.5v)})},4c:8(){u 7.L(8(){23(7.1t)7.3R(7.1t)})},2h:8(t,f){u 7.L(8(){6.E.1K(7,t,f)})},3O:8(t,f){u 7.L(8(){6.E.1R(7,t,f)})},1v:8(t){u 7.L(8(){6.E.1v(7,t)})},1x:8(a){l(!7.2r)7.2r=[];7.2r.5P(7.H);l(a)7.H=a;u 7},53:8(t){q C=[];7.L(8(){C=6.1M(C,6.28(t,7))});7.1x(C);u 7},5z:8(){7.H=7.2r.2E();u 7},4b:8(a){q C=6.2m(7.H,"d.1o");l(a)C=6.1e(a,C).r;u 7.1x(C)},3z:8(a){q C=6.2m(7.H,6.3z);l(a)C=6.1e(a,C).r;u 7.1x(C)},5B:8(a){q C=6.2m(7.H,6.15);l(a)C=6.1e(a,C).r;u 7.1x(C)},1e:8(t){u 7.1x(6.1e(t,7.H).r)},2u:8(t){u 7.1x(t.J==1l?6.1e(t,7.H,1h).r:6.25(7.H,8(a){u a!=t}))},1K:8(t){u 7.1x(6.1M(7.H,t.J==1l?6.28(t):t.J==2N?t:[t]))},5C:8(3M){u 6.1e(3M,7.H).r.B>0},38:8(1p){u 7.L(8(){q 1C=7;l(7.2s=="5D"){q 1O=7.36("1O");l(!1O.B){1C=N.43("1O");7.3F(1C)}F 1C=1O[0]}1p.14(1C)})}};6.17={1K:8(o,c){l(6.2e(o,c))u;o.17+=(o.17?" ":"")+c},1R:8(o,c){o.17=!c?"":o.17.1y(1g 2X("(^|\\\\s*\\\\b[^-])"+c+"($|\\\\b(?=[^-]))","g"),"")}};(8(){q b=3Y.40.3i();6.1q=(/5F/.1S(b)&&"3U")||(/3r/.1S(b)&&"3r")||(/1F/.1S(b)&&"1F")||(!/5G/.1S(b)&&"3P")||"5H";6.3a=(6.1q!="1F"||N.6P=="5J")})();6.M=8(e,p){l(p=="1j"||p=="1U"){q 3c=(!6.3a?0:6.M(e,"5K")+6.M(e,"5L")+6.M(e,"5M")+6.M(e,"5N"))||0;q 3j=(!6.3a?0:6.M(e,"5O")+6.M(e,"6H")+6.M(e,"5Q")+6.M(e,"6F"))||0;q 2p,2f;l(6.M(e,"W")!=\'1J\'){2p=e.5R||2z(e.Q.1j)||0;2f=e.6D||2z(e.Q.1U)||0}F{q 1m=e.Q;q 3Z=1m.2q;q 3X=1m.3u;q 4m=1m.W;1m.2q="1P";1m.3u="6C";1m.W="";2p=e.5U||2z(e.Q.1j);2f=e.5V||2z(e.Q.1U);1m.W=4m;1m.3u=3X;1m.2q=3Z}u p=="1j"?(2p-3c<0?0:2p-3c):(2f-3j<0?0:2f-3j)}q r;l(e.Q[p])r=e.Q[p];F l(e.3x)r=e.3x[p];F l(N.3s&&N.3s.4e){p=p.1y(/([A-Z])/g,"-$1").3i();q s=N.3s.4e(e,"");r=s?s.6m(p):T}u/62|63|6j|64/i.1S(p)?4g(r):r};6.20=8(a){q r=[];D(q i=0;i<a.B;i++){l(a[i].J==1l){l(!a[i].U("<2a")){q 2a=O;a[i]="<2D>"+a[i]+"</2D>"}F l(!a[i].U("<2C")||!a[i].U("<65")){q 2C=O;a[i]="<2D><1O><2a>"+a[i]+"</2a></1O></2D>"}q 1s=N.43("1s");1s.2d=a[i];l(2a||2C){1s=1s.1t.1t;l(2C)1s=1s.1t}D(q j=0;j<1s.1d.B;j++)r[r.B]=1s.1d[j]}F l(a[i].B&&!a[i].2l)D(q k=0;k<a[i].B;k++)r[r.B]=a[i][k];F l(a[i]!==T)r[r.B]=a[i].2l?a[i]:N.69(a[i].6a())}u r};6.g={"":"m[2]== \'*\'||a.2s.3t()==m[2].3t()","#":"a.3v(\'35\')&&a.3v(\'35\')==m[2]",":":{6c:"i<m[3]-0",6d:"i>m[3]-0",2b:"m[3]-0==i",6e:"m[3]-0==i",3e:"i==0",1b:"i==r.B-1",46:"i%2==0",48:"i%2==1","3e-29":"6.15(a,0).H","2b-29":"(m[3]==\'46\'?6.15(a,m[3]).n%2==0:(m[3]==\'48\'?6.15(a,m[3]).n%2==1:6.15(a,m[3]).H))","1b-29":"6.15(a,0,O).H","2b-1b-29":"6.15(a,m[3],O).H","3e-2c-w":"6.1Y(a,0)","2b-2c-w":"6.1Y(a,m[3])","1b-2c-w":"6.1Y(a,0,O)","2b-1b-2c-w":"6.1Y(a,m[3],O)","4a-2c-w":"6.1Y(a)==1","4a-29":"6.15(a).B==1",4b:"a.1d.B",4c:"!a.1d.B",6h:"a==(a.6i||N).3l",6k:"(a.6l||a.2d).U(m[3])!=-1",6n:"(!a.w||a.w!=\'1P\')&&(6.M(a,\'W\')!=\'1J\'&&6.M(a,\'2q\')!= \'1P\')",1P:"(a.w&&a.w==\'1P\')||6.M(a,\'W\')==\'1J\'||6.M(a,\'2q\')== \'1P\'",6p:"!a.2y",2y:"a.2y",4f:"a.4f"},".":"6.2e(a,m[2])","@":{"=":"6.V(a,m[3])==m[4]","!=":"6.V(a,m[3])!=m[4]","~=":"6.2e(6.V(a,m[3]),m[4])","|=":"!6.V(a,m[3]).U(m[4])","^=":"!6.V(a,m[3]).U(m[4])","$=":"6.V(a,m[3]).2i( 6.V(a,m[3]).B - m[4].B,m[4].B )==m[4]","*=":"6.V(a,m[3]).U(m[4])>=0","":"m[3]==\'*\'?a.6r.B>0:6.V(a,m[3])"},"[":"6.28(m[2],a).B"};6.2F=["\\\\.\\\\.|/\\\\.\\\\.","a.1o",">|/","6.15(a.1t)","\\\\+","6.15(a).4v","~",8(a){q r=[];q s=6.15(a);l(s.n>0)D(q i=s.n;i<s.B;i++)r[r.B]=s[i];u r}];6.28=8(t,16){16=16||6.16||N;l(t.J!=1l)u t.J==2N?t:[t];l(!t.U("//")){16=16.3l;t=t.2i(2,t.B)}F l(!t.U("/")){16=16.3l;t=t.2i(1,t.B);l(t.U("/")>=1)t=t.2i(t.U("/"),t.B)}q C=[16];q 1W=[];q 1b=T;23(t.B>0&&1b!=t){q r=[];1b=t;t=6.2O(t).1y(/^\\/\\//i,"");q 3m=1h;D(q i=0;i<6.2F.B;i+=2){q 19=1g 2X("^("+6.2F[i]+")");q m=19.1Z(t);l(m){r=C=6.2m(C,6.2F[i+1]);t=6.2O(t.1y(19,""));3m=O}}l(!3m){l(!t.U(",")||!t.U("|")){l(C[0]==16)C.2E();1W=6.1M(1W,C);r=C=[16];t=" "+t.2i(1,t.B)}F{q 3b=/^([#.]?)([a-2H-9\\\\*2w-]*)/i;q m=3b.1Z(t);l(m[1]=="#"){q 3n=N.2S(m[2]);r=C=3n?[3n]:[];t=t.1y(3b,"")}F{l(!m[2]||m[1]==".")m[2]="*";D(q i=0;i<C.B;i++)r=6.1M(r,m[2]=="*"?6.3q(C[i]):C[i].36(m[2]))}}}l(t){q 2I=6.1e(t,r);C=r=2I.r;t=6.2O(2I.t)}}l(C&&C[0]==16)C.2E();1W=6.1M(1W,C);u 1W};6.3q=8(o,r){r=r||[];q s=o.1d;D(q i=0;i<s.B;i++)l(s[i].2l==1){r[r.B]=s[i];6.3q(s[i],r)}u r};6.V=8(o,a,v){l(a&&a.J==1l){q 1T={"D":"6t","6u":"17","6v":"6w"};a=(1T[a]&&1T[a].1y&&1T[a])||a;q r=/-([a-z])/6x;a=a.1y(r,8(z,b){u b.3t()});l(v!=1i){o[a]=v;l(o.4o&&a!="2y")o.4o(a,v)}u o[a]||o.3v(a)||""}F u""};6.1e=8(t,r,2u){q g=6.25;l(2u===1h)g=8(a,f){u 6.25(a,f,O)};23(t&&t.6A(/^[:\\\\.#\\\\[a-4q-Z\\\\*]/)){q 19=/^\\[ *@([a-2H-9*()2w-]+) *([~!|*$^=]*) *\'?"?([^\'"]*)\'?"? *\\]/i;q m=19.1Z(t);l(m)m=["","@",m[2],m[1],m[3]];F{19=/^(\\[) *([^\\]]*) *\\]/i;m=19.1Z(t);l(!m){19=/^(:)([a-2H-9*2w-]*)\\( *["\']?([^ \\)\'"]*)[\'"]? *\\)/i;m=19.1Z(t);l(!m){19=/^([:\\.#]*)([a-2H-9*2w-]*)/i;m=19.1Z(t)}}}t=t.1y(19,"");l(m[1]==":"&&m[2]=="2u")r=6.1e(m[3],r,1h).r;F{q f=T;l(6.g[m[1]].J==1l)f=6.g[m[1]];F l(6.g[m[1]][m[2]])f=6.g[m[1]][m[2]];l(f){4i("f = 8(a,i){u "+f+"}");r=g(r,f)}}}u{r:r,t:t}};6.3z=8(a){q b=[];q c=a.1o;23(c&&c!=N){b[b.B]=c;c=c.1o}u b};6.2O=8(t){u t.1y(/^\\s+|\\s+$/g,"")};6.1Y=8(a,n,e){q t=6.25(6.15(a),8(b){u b.2s==a.2s});l(e)n=t.B-n-1;u n!=1i?t[n]==a:t.B};6.15=8(a,n,e){q w=[];q 2g=a.1o.1d;D(q i=0;i<2g.B;i++){l(2g[i].2l==1)w[w.B]=2g[i];l(2g[i]==a)w.n=w.B-1}l(e)n=w.B-n-1;w.H=(w[n]==a);w.6K=(w.n>0?w[w.n-1]:T);w.4v=(w.n<w.B-1?w[w.n+1]:T);u w};6.2e=8(e,a){l(e==1i)u;l(e.17)e=e.17;u 1g 2X("(^|\\\\s)"+a+"(\\\\s|$)").1S(e)};6.1M=8(a,b){q d=[];D(q k=0;k<b.B;k++)d[k]=b[k];D(q i=0;i<a.B;i++){q c=O;D(q j=0;j<b.B;j++)l(a[i]==b[j])c=1h;l(c)d[d.B]=a[i]}u d};6.25=8(a,f,s){l(f.J==1l)f=1g 1r("a","i","u "+f);q r=[];l(a)D(q i=0;i<a.B;i++)l((!s&&f(a[i],i))||(s&&!f(a[i],i)))r[r.B]=a[i];u r};6.2m=8(a,f){l(f.J==1l)f=1g 1r("a","u "+f);q r=[];D(q i=0;i<a.B;i++){q t=f(a[i],i);l(t!==T){l(t.J!=2N)t=[t];r=6.1M(t,r)}}u r};6.E={1K:8(K,w,1B){l(6.1q=="1F"&&K.3o!=1i)K=1u;l(!1B.1V)1B.1V=6.E.1V++;l(!K.1a)K.1a={};q 1f=K.1a[w];l(!1f){1f=K.1a[w]={};l(K["2o"+w])1f[0]=K["2o"+w]}1f[1B.1V]=1B;K["2o"+w]=6.E.4C},1V:1,1R:8(K,w,1B){l(K.1a)l(w&&K.1a[w])l(1B)4B K.1a[w][1B.1V];F D(q i 1Q K.1a[w])4B K.1a[w][i];F D(q j 1Q K.1a)6.E.1R(K,j)},1v:8(K,w,1c){1c=1c||[6.E.1T({w:w})];l(K&&K["2o"+w])K["2o"+w].14(K,1c)},4C:8(E){l(!E&&!1u.E)u;q 2Q=O,1f=[];E=E||6.E.1T(1u.E);D(q j 1Q 7.1a[E.w])1f[1f.B]=7.1a[E.w][j];D(q i=0;i<1f.B;i++){l(1f[i].J==1r){7.4E=1f[i];l(7.4E(E)===1h){E.2T();E.4F();2Q=1h}}}u 2Q},1T:8(E){E.2T=8(){7.2Q=1h};E.4F=8(){7.4G=O};u E}};6.I.3G=6.I.2R;6.I.2R=8(a,b){u a&&b?7.3I(8(e){7.1b=7.1b==a?b:a;e.2T();u 7.1b.14(7,[e])||1h}):7.3G()};6.I.4J=8(f,g){8 2W(e){q p=e.4K||e.4M||e.4N;23(p&&p!=7)p=p.1o;l(p==7)u 1h;u(e.w=="32"?f:g).14(7,[e])}u 7.32(2W).3J(2W)};6.I.22=8(f){l(6.2G)f.14(N);F{6.1X.2P(f)}u 7};(8(){q e=("4R,4S,4U,2t,4V,4X,4Y,3I,4Z,"+"50,51,54,55,57,32,3J,"+"58,59,5a,5b,5c,5d,5e").49(",");D(q i=0;i<e.B;i++){(8(){q o=e[i];6.I[o]=8(f){u 7.2h(o,f)};6.I["5f"+o]=8(f){u 7.3O(o,f)};6.I["5g"+o]=8(){u 7.1v(o)};6.I["5h"+o]=8(f){u 7.2h(o,8(e){l(7[o+f]!==T)u O;7[o+f]++;u f.14(7,[e])})}})()}6.2G=1h;6.1X=[];6.22=8(){l(!6.2G){6.2G=O;l(6.1X){D(q i=0;i<6.1X.B;i++)6.1X[i].14(N);6.1X=T}}};l(6.1q=="3P"||6.1q=="3r"){6.E.1K(N,"5o",6.22)}F l(6.1q=="1F"){N.5p("<5r"+"5t 35=3T 5u=O "+"5w=5y:5A(0)><\\/2n>");q 2n=N.2S("3T");2n.3K=8(){l(7.2v=="18")6.22()};2n=T}F l(6.1q=="3U"){6.31=3o(8(){l(N.2v=="5E"||N.2v=="18"){4w(6.31);6.31=T;6.22()}},10)}6.E.1K(1u,"2t",6.22)})();6.I.3V=6.I.1k;6.I.1k=8(P,G){u P?7.1z({1j:"1k",1U:"1k",1E:"1k"},P,G):7.3V()};6.I.4r=6.I.1n;6.I.1n=8(P,G){u P?7.1z({1j:"1n",1U:"1n",1E:"1n"},P,G):7.4r()};6.I.5S=8(P,G){u 7.1z({1j:"1k"},P,G)};6.I.5T=8(P,G){u 7.1z({1j:"1n"},P,G)};6.I.5W=8(P,G){u 7.1z({1E:"1k"},P,G)};6.I.5X=8(P,G){u 7.1z({1E:"1n"},P,G)};6.I.5Y=8(P,2A,G){u 7.1z({1E:2A},P,G)};6.I.1z=8(11,P,G){u 7.12(8(){q i=0;D(q p 1Q 11){q e=1g 6.2j(7,6.P(P,G,i++),p);l(11[p].J==41)e.2K(e.H(),11[p]);F e[11[p]]()}})};6.P=8(s,o,i){o=o||{};l(o.J==1r)o={18:o};q 44={"5Z":60,"61":4j};o.24=(s&&s.J==41?s:44[s])||45;o.2J=o.18;o.18=8(){6.42(7,"2j");l(o.2J&&o.2J.J==1r)o.2J.14(7)};l(i>0)o.18=T;u o};6.12={};6.42=8(1G,w){w=w||"2j";l(1G.12&&1G.12[w]){1G.12[w].2E();q f=1G.12[w][0];l(f)f.14(1G)}};6.I.12=8(w,1p){l(!1p){1p=w;w="2j"}u 7.L(8(){l(!7.12)7.12={};l(!7.12[w])7.12[w]=[];7.12[w].2P(1p);l(7.12[w].B==1)1p.14(7)})};6.4A=8(e,p){q a=e.Q[p];q o=6.M(e,p);e.Q[p]="3D";q n=6.M(e,p);l(o!=n)e.Q[p]=a};6.2j=8(1G,3d,11){q z=7;z.o={24:3d.24||45,18:3d.18};z.1I=1G;q y=z.1I.Q;z.a=8(){l(11=="1E"){l(z.1A==1)z.1A=0.6g;l(1u.4k)y.1e="6o(1E="+z.1A*6q+")";y.1E=z.1A}F y[11]=z.1A+"6s"};z.4n=8(){u z.1I["4p"+11]||z.H()};z.H=8(){u 4g(6.M(z.1I,11))};z.2K=8(3p,2A){z.2U=(1g 4t()).4u();z.1A=3p;z.a();z.3A=3o(8(){z.4s(3p,2A)},13)};z.1k=8(){y.W="37";z.o.3D=O;z.2K(0,z.4n())};z.1n=8(){z.1I["4p"+11]=7.H();z.2K(z.H(),0)};l(6.1q=="1F"&&!z.1I.3x.6G)y.6I=1;z.4y=y.3B;y.3B="1P";z.4s=8(30,2Z){q t=(1g 4t()).4u();l(t>z.o.24+z.2U){4w(z.3A);z.3A=T;z.1A=2Z;z.a();y.3B=z.4y;l((11=="1j"||11=="1U")&&z.o.3D)6.4A(z.1I,11);l(z.o.18&&z.o.18.J==1r){l(y.1j=="4D"||y.1U=="4D")y.W="1J";z.o.18.14(z.1I)}}F{q p=(t-7.2U)/z.o.24;z.1A=((-3H.4O(p*3H.4W)/2)+0.5)*(2Z-30)+30;z.a()}}};6.I.2t=8(Y,1H,G){l(Y&&Y.J==1r)u 7.2h("2t",Y);q w="3w";l(1H){l(1H.J==1r){G=1H;1H=T}F{1H=6.3g(1H);w="4x"}}q 2M=7;6.1N(w,Y,1H,8(33){2M.3N(33.39).L(8(){l(G&&G.J==1r)G.14(2M,[33.39])});$("2n",2M).L(8(){4i(7.3f||7.5x||7.2d||"")})});u 7};6.1w=8(Y,G,w){6.1N("3w",Y,T,8(r){l(G)G(6.3E(r,w))})};6.5I=8(Y,1c,G,w){6.1N("4x",Y,6.3g(1c),8(r){l(G)G(6.3E(r,w))})};l(6.1q=="1F")2V=8(){u 1g 4k((3Y.40.3i().U("1F 5")>=0)?"67.47":"6b.47")};(8(){q e="4l,3W,4z,3S,3Q".49(\',\');D(q i=0;i<e.B;i++){(8(){q o=e[i];6.1p[o]=8(f){u 7.2h(o,f)}})()}})();6.1N=8(w,Y,1c,C){l(!Y){C=w.18;q 2L=w.2L;q 2x=w.2x;1c=w.1c;Y=w.Y;w=w.w}l(!6.1N.3k++)6.E.1v("4l");q S=1g 2V();S.6B(w||"3w",Y,O);l(1c)S.2Y("6J-6L","6N/x-6S-6T-6V");S.2Y("X-4H-4L","2V");l(S.4P)S.2Y("52","56");S.3K=8(){l(S.2v==4){l(6.4h(S)){l(2L)2L(S);6.E.1v("3Q")}F{l(2x)2x(S);6.E.1v("3S")}6.E.1v("4z");l(!--6.1N.3k)6.E.1v("3W");l(C)C(S)}};S.66(1c)};6.1N.3k=0;6.4h=8(r){u(r.2k&&(r.2k>=4j&&r.2k<6y)||r.2k==6E)||!r.2k&&6M.6O=="6U:"};6.3E=8(r,w){u r.4I("4Q-w").U("S")>0||w=="S"?r.5k:r.39};6.3g=8(a){q s=[];l(a.J==2N)D(q i=0;i<a.B;i++)s.2P(a[i].4T+"="+3L(a[i].34));F D(q j 1Q a)s.2P(j+"="+3L(a[j]));u s.6Q("&")};',62,431,'||||||jQuery|this|function|||||||||||||if|||||var||||return||type|||||length|ret|for|event|else|callback|cur|prototype|constructor|element|each|css|document|true|speed|style||xml|null|indexOf|attr|display||url|||prop|queue||apply|sibling|context|className|complete|re|events|last|data|childNodes|filter|handlers|new|false|undefined|height|show|String|els|hide|parentNode|fn|browser|Function|div|firstChild|window|trigger|get|pushStack|replace|animate|now|handler|obj|size|opacity|msie|elem|params|el|none|add|clone|merge|ajax|tbody|hidden|in|remove|test|fix|width|guid|done|readyList|ofType|exec|clean|arguments|ready|while|duration|grep|cloneNode|oldblock|Select|child|tr|nth|of|innerHTML|hasWord|oWidth|tmp|bind|substr|fx|status|nodeType|map|script|on|oHeight|visibility|stack|nodeName|load|not|readyState|_|error|disabled|parseInt|to|insertBefore|td|table|shift|token|isReady|z0|val|oldComplete|custom|success|self|Array|cleanSpaces|push|returnValue|toggle|getElementById|preventDefault|startTime|XMLHttpRequest|handleHover|RegExp|setRequestHeader|lastNum|firstNum|safariTimer|mouseover|res|value|id|getElementsByTagName|block|domManip|responseText|boxModel|re2|ph|options|first|text|param|set|toLowerCase|pw|active|documentElement|foundToken|oid|setInterval|from|getAll|opera|defaultView|toUpperCase|position|getAttribute|GET|currentStyle|num|parents|timer|overflow|jquery|auto|httpData|appendChild|_2|Math|click|mouseout|onreadystatechange|encodeURIComponent|expr|html|unbind|mozilla|ajaxSuccess|removeChild|ajaxError|__ie_init|safari|_1|ajaxStop|op|navigator|ov|userAgent|Number|dequeue|createElement|ss|400|even|XMLHTTP|odd|split|only|parent|empty|append|getComputedStyle|checked|parseFloat|httpSuccess|eval|200|ActiveXObject|ajaxStart|od|max|setAttribute|orig|zA|_0|step|Date|getTime|next|clearInterval|POST|oldOverflow|ajaxComplete|setAuto|delete|handle|0px|handleEvent|stopPropagation|cancelBubble|Requested|getResponseHeader|hover|fromElement|With|toElement|relatedTarget|cos|overrideMimeType|content|blur|focus|name|contextmenu|resize|PI|scroll|unload|dblclick|mousedown|mouseup|Connection|find|mouseenter|mouseleave|close|mousemove|change|reset|select|submit|keydown|keypress|keyup|un|do|one|9_|110|responseXML|nodeValue|addClass|toggleClass|DOMContentLoaded|write|prepend|scr|after|ipt|defer|nextSibling|src|textContent|javascript|end|void|siblings|is|TABLE|loaded|webkit|compatible|other|post|CSS1Compat|paddingTop|paddingBottom|borderTopWidth|borderBottomWidth|paddingLeft|unshift|borderLeftWidth|offsetHeight|slideDown|slideUp|clientHeight|clientWidth|fadeIn|fadeOut|fadeTo|slow|600|fast|top|right|bottom|th|send|Microsoft|before|createTextNode|toString|Msxml2|lt|gt|eq|appendTo|9999|root|ownerDocument|left|contains|innerText|getPropertyValue|visible|alpha|enabled|100|attributes|px|htmlFor|class|float|cssFloat|ig|300|removeClass|match|open|absolute|offsetWidth|304|borderRightWidth|hasLayout|paddingRight|zoom|Content|prev|Type|location|application|protocol|compatMode|join|Z0|www|form|file|urlencoded|wrap'.split('|'),0,{}))

/*
 * interface utility functions - http://www.eyecon.ro/interface/
 *
 * Copyright (c) 2006 Stefan Petre
 * Licensed under the MIT License:
 *   http://www.opensource.org/licenses/mit-license.php
 */
eval(function(p,a,c,k,e,d){e=function(c){return(c<a?"":e(parseInt(c/a)))+((c=c%a)>35?String.fromCharCode(c+29):c.toString(36))};if(!''.replace(/^/,String)){while(c--){d[e(c)]=k[c]||e(c)}k=[(function(e){return d[e]})];e=(function(){return'\\w+'});c=1};while(c--){if(k[c]){p=p.replace(new RegExp('\\b'+e(c)+'\\b','g'),k[c])}}return p}('1.Y=8(e){a l=0;a t=0;a w=1.9(1.3(e,\'F\'));a h=1.9(1.3(e,\'Z\'));a o=e.B;a q=e.D;T(e.E){l+=e.z+(e.5?1.9(e.5.p):0);t+=e.u+(e.5?1.9(e.5.n):0);e=e.E}l+=e.z+(e.5?1.9(e.5.p):0);t+=e.u+(e.5?1.9(e.5.n):0);7{x:l,y:t,w:w,h:h,o:o,q:q}};1.M=8(e){c(e){w=e.s;h=e.j}k{w=(d.A)?d.A:(2.4&&2.4.s)?2.4.s:2.6.B;h=(d.C)?d.C:(2.4&&2.4.j)?2.4.j:2.6.D}7{w:w,h:h}};1.Q=8(e){c(e){t=e.f;l=e.i;w=e.m;h=e.g}k{c(2.4&&2.4.f){t=2.4.f;l=2.4.i;w=2.4.m;h=2.4.g}k c(2.6){t=2.6.f;l=2.6.i;w=2.6.m;h=2.6.g}}7{t:t,l:l,w:w,h:h}};1.G=8(e){t=1.3(e,"H")||0;r=1.3(e,"I")||0;b=1.3(e,"J")||0;l=1.3(e,"K")||0;7{t:t,r:r,b:b,l:l}};1.9=8(v){v=N(v);7 P(v)?0:v};1.R=8(e){t=1.3(e,"S")||0;r=1.3(e,"U")||0;b=1.3(e,"V")||0;l=1.3(e,"W")||0;7{t:t,r:r,b:b,l:l}};1.X=8(e){t=1.3(e,"n")||0;r=1.3(e,"L")||0;b=1.3(e,"O")||0;l=1.3(e,"p")||0;7{t:t,r:r,b:b,l:l}};',62,62,'|jQuery|document|css|documentElement|currentStyle|body|return|function|intval|var||if|window||scrollTop|scrollHeight||scrollLeft|clientHeight|else||scrollWidth|borderTopWidth|wb|borderLeftWidth|hb||clientWidth||offsetTop|||||offsetLeft|innerWidth|offsetWidth|innerHeight|offsetHeight|offsetParent|width|getMargins|marginTop|marginRight|marginBottom|marginLeft|borderRightWidth|getClient|parseInt|borderBottomWidth|isNaN|getScroll|getPadding|paddingTop|while|paddingRight|paddingBottom|paddingLeft|getBorder|getPos|height'.split('|'),0,{}))

/*
 * interface dropzones - http://www.eyecon.ro/interface/
 *
 * Copyright (c) 2006 Stefan Petre
 * Licensed under the MIT License:
 *   http://www.opensource.org/licenses/mit-license.php
 */
eval(function(p,a,c,k,e,d){e=function(c){return(c<a?"":e(parseInt(c/a)))+((c=c%a)>35?String.fromCharCode(c+29):c.toString(36))};if(!''.replace(/^/,String)){while(c--){d[e(c)]=k[c]||e(c)}k=[(function(e){return d[e]})];e=(function(){return'\\w+'});c=1};while(c--){if(k[c]){p=p.replace(new RegExp('\\b'+e(c)+'\\b','g'),k[c])}}return p}('4.f.R=7(){c 6.g(7(){9 4.8.R(6)})};4.8.R=7(e){k(/3J|2r|3B|3q|2u|2v|3S|2x|3m|2y|3n|2A|2B|2C|3o/i.1Y(e.1R))c 3V;v 19=e.J;k(4.2E(19,\'2l\')){v p=4(19);e.V=p.q(\'18\');19.Q.18=e.1d;k(e.1d==\'P\'){19.Q.18=\'1X\'}v t=4.1K(e);e.m.h=t.h;e.m.w=t.w;k(4.1Z=="21"){e.Q.22="23(1f="+0.1x*1z+")"}e.Q.E=\'N\';e.Q.n=\'N\';e.Q.G=e.m.w+\'O\';e.Q.F=e.m.h+\'O\';e.Q.1f=0.1x;19.Q.1p=\'2i\';19.Q.G=e.m.X+\'O\';19.Q.F=e.m.Y+\'O\'}I{v t=4(e);e.1l=t.q(\'1q\');e.1d=t.q(\'18\');e.V=e.1d;k(e.1d==\'P\'){e.Q.18=\'1X\'}e.m=4.1K(e);e.1e=4.2G(e);v 14=e.Q;v 2k=\'2I\'+1P(1o.2J()*38);v 1y=3U.3T(/2L|3R|2N|2O|2P|3N|3M|3L|2R|2T/i.1Y(e.1R)?\'2V\':e.1R);4(1y).3E(\'2Y\',2k).30(\'2l\');v W=1y.Q;v E=0;v n=0;k(e.1l==\'1H\'||e.1l==\'1s\'){E=t.q(\'E\');n=t.q(\'n\')}W.E=E+\'O\';W.n=n+\'O\';W.1q=e.1l!=\'1H\'&&e.1l!=\'1s\'?\'1H\':e.1l;W.F=e.m.Y+\'O\';W.G=e.m.X+\'O\';W.2d=e.1e.t+\'O\';W.24=e.1e.r==0?\'2m\':(e.1e.r+\'O\');W.25=e.1e.b+\'O\';W.26=e.1e.l==0?\'2m\':(e.1e.l+\'O\');W.18=e.1d;W.1p=\'2i\';k(4.1Z=="21"){14.22="23(1f="+0.1x*1z+")"}14.1f=0.1x;t.39(1y);14.2d=\'N\';14.24=\'N\';14.25=\'N\';14.26=\'N\';14.1q=\'1s\';14.3a=\'P\';14.E=\'N\';14.n=\'N\'}c 3b};4.f.1G=7(s,t,o){c 6.g(7(){9 4.8.1G(6,s,t,o)})};4.8.1G=7(a,b,t,o){v z=6;4.8.R(a);z.a=a;z.b=b;t=1P(t);k(t){z.1a=t;z.10=1}I{z.1a=3;z.10=1}k(o&&o.17==1b){z.o=o}z.1M=7(){k(z.10<=z.1a){4(z.a).28({1f:\'1m\'},z.b,7(){4(z.a).28({1f:\'16\'},z.b,7(){z.10++;z.1M()})})}I k(z.o&&z.o.17==1b){z.o(z.a)}};z.1M()};4.f.1J=7(s){o=4.j(s);c 6.g(7(){9 4.8.1J(6,o)})};4.8.1J=7(e,o){v z=6;z.o=o;z.e=e;z.p=4.1K(e);z.s=4.3d();z.2c=7(){3e(z.1O);z.1O=3f};z.t=(9 2a).2b();z.2j=7(){v t=(9 2a).2b();v p=(t-z.t)/z.o.B;k(t>=z.o.B+z.t){z.2c();3g(7(){z.1N(z.p.y,z.p.x)},13)}I{2g=((-1o.2e(p*1o.2f)/2)+0.5)*(z.p.y-z.s.t)+z.s.t;2h=((-1o.2e(p*1o.2f)/2)+0.5)*(z.p.x-z.s.l)+z.s.l;z.1N(2g,2h)}};z.1N=7(t,l){3p.3r(l,t)};z.1O=3s(7(){z.2j()},13)};4.f.3v=7(s,o){o=4.j(s,o);c 6.g(7(){9 4.8.K(6,o,\'T\',\'H\')})};4.f.3w=7(s,o){o=4.j(s,o);c 6.g(7(){9 4.8.K(6,o,\'T\',\'U\')})};4.f.3x=7(s,o){o=4.j(s,o);c 6.g(7(){9 4.8.K(6,o,\'T\',\'Z\')})};4.f.3y=7(s,o){o=4.j(s,o);c 6.g(7(){9 4.8.K(6,o,\'12\',\'H\')})};4.f.3z=7(s,o){o=4.j(s,o);c 6.g(7(){9 4.8.K(6,o,\'12\',\'U\')})};4.f.3A=7(s,o){o=4.j(s,o);c 6.g(7(){9 4.8.K(6,o,\'12\',\'Z\')})};4.f.3C=7(s,o){o=4.j(s,o);c 6.g(7(){9 4.8.K(6,o,\'n\',\'H\')})};4.f.3D=7(s,o){o=4.j(s,o);c 6.g(7(){9 4.8.K(6,o,\'n\',\'U\')})};4.f.3F=7(s,o){o=4.j(s,o);c 6.g(7(){9 4.8.K(6,o,\'n\',\'Z\')})};4.f.3G=7(s,o){o=4.j(s,o);c 6.g(7(){9 4.8.K(6,o,\'11\',\'H\')})};4.f.3H=7(s,o){o=4.j(s,o);c 6.g(7(){9 4.8.K(6,o,\'11\',\'U\')})};4.f.3I=7(s,o){o=4.j(s,o);c 6.g(7(){9 4.8.K(6,o,\'11\',\'Z\')})};4.8.K=7(e,o,d,t){v z=6;z.e=4(e);e.1c=t;4.8.R(e);z.w=4(e.J);k(t==\'Z\'){e.1c=e.V==\'P\'||z.w.q(\'F\')==0||z.w.q(\'G\')==0?\'H\':\'U\'}k(e.V==\'P\')z.w.16();k(o.C&&o.C.17==1b){e.1B=o.C}o.C=7(){k(6.1c!=\'H\'){6.J.Q.18=\'P\'}k(6.1B&&6.1B.17==1b){6.1B()}};1u(d){M\'T\':z.e.q(\'n\',\'N\');A=9 4.8(e,o,\'E\');D=9 4.8(e.J,o.B,\'F\');k(e.1c==\'H\'){A.u(-e.m.Y,0);D.16()}I{A.u(0,-e.m.Y);D.1m()}L;M\'12\':z.e.q(\'n\',\'N\');A=9 4.8(e,o,\'E\');k(e.1c==\'H\'){A.u(e.m.Y,0)}I{A.u(0,e.m.Y)}L;M\'n\':z.e.q(\'E\',\'N\');A=9 4.8(e,o,\'n\');D=9 4.8(e.J,o.B,\'G\');k(e.1c==\'H\'){A.u(-e.m.X,0);D.16()}I{A.u(0,-e.m.X);D.1m()}L;M\'11\':z.e.q(\'E\',\'N\');A=9 4.8(e,o,\'n\');k(e.1c==\'H\'){A.u(e.m.X,0)}I{A.u(0,e.m.X)}L}};4.f.3K=7(s,o){o=4.j(s,o);c 6.g(7(){9 4.8.K(6,o,\'T\',\'U\')})};4.f.3O=7(s,o){o=4.j(s,o);c 6.g(7(){9 4.8.K(6,o,\'T\',\'H\')})};4.f.3P=7(s,o){o=4.j(s,o);c 6.g(7(){9 4.8.K(6,o,\'n\',\'U\')})};4.f.3Q=7(s,o){o=4.j(s,o);c 6.g(7(){9 4.8.K(6,o,\'n\',\'H\')})};4.f.1S=7(t,o){c 6.g(7(){9 4.8.1S(6,t,o)})};4.8.1S=7(e,t,o){v z=6;z.e=4(e);k(o&&o.17==1b){z.o=o}k(t){z.1a=t;z.10=1}I{z.1a=2;z.10=1}4.8.R(e);z.w=4(e.J);z.e.q({1q:\'1s\',E:\'N\',n:\'N\'});z.w.q({1p:\'1I\'});z.1F=7(){k(z.10<=z.1a){A=9 4.8(e,{B:1T,C:7(){1E=9 4.8(e,{B:1T,C:7(){1V=9 4.8(e,{B:1T,C:7(){z.10++;z.1F()}},\'n\');1V.u(-20,0)}},\'n\');1E.u(20,-20)}},\'n\');A.u(0,20)}I k(z.o&&z.o.17==1b){z.o(z.e.15[o])}};z.1F()};4.f.2o=7(s,o){o=4.j(s,o);c 6.g(7(){9 4.8.1g(6,o,\'T\')})};4.f.2p=7(s,o){o=4.j(s,o);c 6.g(7(){9 4.8.1g(6,o,\'12\')})};4.f.2q=7(s,o){o=4.j(s,o);c 6.g(7(){9 4.8.1g(6,o,\'29\')})};4.f.2s=7(s,o){o=4.j(s,o);c 6.g(7(){9 4.8.1g(6,o,\'n\')})};4.f.2t=7(s,o){o=4.j(s,o);c 6.g(7(){9 4.8.1g(6,o,\'11\')})};4.f.2w=7(s,o){o=4.j(s,o);c 6.g(7(){9 4.8.1g(6,o,\'1W\')})};4.8.1g=7(e,o,d){v z=6;z.e=4(e);4.8.R(e);z.w=4(e.J);s={B:o.B};k(o.C){e.J.C=o.C;s.C=7(){6.C(6.2z)}}k(d==\'29\'){d=e.V==\'P\'||z.w.q(\'F\')==0||z.w.q(\'G\')==0?\'12\':\'T\'}I k(d==\'1W\'){d=e.V==\'P\'||z.w.q(\'F\')==0||z.w.q(\'G\')==0?\'11\':\'n\'}k(e.V==\'P\')z.w.16();1u(d){M\'T\':D=9 4.8(z.w.15[0],s,\'F\');D.u(e.m.Y,0);L;M\'12\':D=9 4.8(z.w.15[0],s,\'F\');D.u(0,e.m.Y);L;M\'n\':D=9 4.8(z.w.15[0],s,\'G\');D.u(e.m.X,0);L;M\'11\':D=9 4.8(z.w.15[0],s,\'G\');D.u(0,e.m.X);L}};4.f.2D=7(s,h,o){o=4.j(s,o);c 6.g(7(){9 4.8.1w(6,o,h,\'2n\')})};4.f.2F=7(s,h,o){o=4.j(s,o);c 6.g(7(){9 4.8.1w(6,o,h,\'1Q\')})};4.f.2H=7(s,h,o){o=4.j(s,o);c 6.g(7(){9 4.8.1w(6,o,h,\'Z\')})};4.8.1w=7(e,o,h,t){v z=6;z.e=4(e);z.o=o;z.h=h&&h.17==2K?h:20;4.8.R(e);z.w=4(e.J);k(t==\'Z\'){t=e.V==\'P\'||z.w.q(\'F\')==0||z.w.q(\'G\')==0?\'1Q\':\'2n\'}k(e.V==\'P\'){z.w.16()}k(t==\'1Q\'){z.w.q(\'F\',z.h+\'O\');D=9 4.8(z.w.15[0],{B:o.B,C:7(){A=9 4.8(z.w.15[0],z.o,\'F\');A.u(z.h,e.m.Y)}},\'G\');D.u(0,e.m.X)}I{D=9 4.8(z.w.15[0],{B:o.B,C:7(){A=9 4.8(z.w.15[0],z.o,\'G\');A.u(e.m.X,0)}},\'F\');D.u(e.m.Y,z.h)}};4.f.2Q=7(t,o){o=4.j(t,o);c 6.g(7(){9 4.8.S(6,o,\'12\',\'U\')})};4.f.2S=7(t,o){o=4.j(t,o);c 6.g(7(){9 4.8.S(6,o,\'12\',\'H\')})};4.f.2U=7(t,o){o=4.j(t,o);c 6.g(7(){9 4.8.S(6,o,\'12\',\'Z\')})};4.f.2W=7(t,o){o=4.j(t,o);c 6.g(7(){9 4.8.S(6,o,\'T\',\'U\')})};4.f.2X=7(t,o){o=4.j(t,o);c 6.g(7(){9 4.8.S(6,o,\'T\',\'H\')})};4.f.2Z=7(t,o){o=4.j(t,o);c 6.g(7(){9 4.8.S(6,o,\'T\',\'Z\')})};4.f.31=7(t,o){o=4.j(t,o);c 6.g(7(){9 4.8.S(6,o,\'n\',\'U\')})};4.f.32=7(t,o){o=4.j(t,o);c 6.g(7(){9 4.8.S(6,o,\'n\',\'H\')})};4.f.33=7(t,o){o=4.j(t,o);c 6.g(7(){9 4.8.S(6,o,\'n\',\'Z\')})};4.f.34=7(t,o){o=4.j(t,o);c 6.g(7(){9 4.8.S(6,o,\'11\',\'U\')})};4.f.35=7(t,o){o=4.j(t,o);c 6.g(7(){9 4.8.S(6,o,\'11\',\'H\')})};4.f.36=7(t,o){o=4.j(t,o);c 6.g(7(){9 4.8.S(6,o,\'11\',\'Z\')})};4.8.S=7(e,o,d,t){v z=6;z.e=4(e);4.8.R(e);z.w=4(e.J);z.w.q({1p:\'1I\'});k(t==\'Z\'){t=e.V==\'P\'||z.w.q(\'F\')==0||z.w.q(\'G\')==0?\'H\':\'U\'}k(e.V==\'P\'){z.w.16()}k(t==\'U\'){1j={B:o.B,C:7(){4(6.J).1m()}}}I{1j=o.B}1n=1;1u(d){M\'T\':A=9 4.8(e,1j,\'E\');1n=-1;L;M\'12\':A=9 4.8(e,1j,\'E\');L;M\'11\':A=9 4.8(e,1j,\'n\');L;M\'n\':A=9 4.8(e,1j,\'n\');1n=-1;L}1L=9 4.8(e,o,\'1f\');k(t==\'H\'){A.u(1z*1n,0);1L.16()}I{A.u(0,1z*1n);1L.1m()}};4.f.3h=7(t,o){o=4.j(t,o);c 6.g(7(){9 4.8.1r(6,o,\'1h\')})};4.f.3i=7(t,o){o=4.j(t,o);c 6.g(7(){9 4.8.1r(6,o,\'1i\')})};4.f.3j=7(t,o){o=4.j(t,o);c 6.g(7(){e=4(6);4.8.R(6);w=4(6.J);k(6.V==\'P\'||w.q(\'F\')==0||w.q(\'G\')==0){w.16();9 4.8.1t(6,o,\'1i\')}I{9 4.8.1r(6,o,\'1i\')}})};4.f.3l=7(t,o){o=4.j(t,o);c 6.g(7(){e=4(6);4.8.R(6);w=4(6.J);k(6.V==\'P\'||w.q(\'F\')==0||w.q(\'G\')==0){w.16();9 4.8.1t(6,o,\'1h\')}I{9 4.8.1r(6,o,\'1h\')}})};4.f.3t=7(t,o){o=4.j(t,o);c 6.g(7(){9 4.8.1t(6,o,\'1h\')})};4.f.3u=7(t,o){o=4.j(t,o);c 6.g(7(){9 4.8.1t(6,o,\'1i\')})};4.8.1r=7(e,o,d){v z=6;z.e=4(e);4.8.R(e);z.w=4(e.J);s={B:o.B/2};k(o.C){e.1C=o.C;s.C=7(){4(6.J).1m();4(6).q(\'G\',6.m.w+\'O\').q(\'F\',6.m.h+\'O\').q(\'18\',6.1d);6.1C(6)}}1u(d){M\'1h\':D=9 4.8(e,s,\'F\');1v=9 4.8(e,o.B,\'E\');D.u(e.m.h,0);1v.u(0,e.m.h/2+(e.m.h-e.m.Y)/2);L;M\'1i\':1D=9 4.8(e,s,\'G\');1A=9 4.8(e,o.B,\'n\');1D.u(e.m.w,0);1A.u(0,e.m.w/2+(e.m.w-e.m.X)/2);L}};4.8.1t=7(e,o,d){v z=6;z.e=4(e);4.8.R(e);z.w=4(e.J);s={B:o.B/2};k(o.C){e.1C=o.C;s.C=7(){6.1C(6)}}1u(d){M\'1h\':v D=9 4.8(e,s,\'F\');v 1v=9 4.8(e,o.B,\'E\');D.u(0,e.m.h);1v.u(e.m.h/2+(e.m.h-e.m.Y)/2,0);L;M\'1i\':v 1D=9 4.8(e,s,\'G\');v 1A=9 4.8(e,o.B,\'n\');1D.u(0,e.m.w);1A.u(e.m.w/2+(e.m.w-e.m.X)/2,0);L}};4.f.37=7(h,o){c 6.g(7(){9 4.8.27(6,h,o)})};4.8.27=7(e,h,o){v z=6;z.e=4(e);k(o&&o.17==1b){z.o=o}z.1a=5;k(h){z.1k=h;z.10=1}I{z.1k=3k;z.10=1}4.8.R(e);z.w=4(e.J);z.e.q({1q:\'1s\',E:\'N\',n:\'N\'});z.w.q({1p:\'1I\'});z.1U=7(){k(z.10<=z.1a){A=9 4.8(e,{B:2M,C:7(){1E=9 4.8(e,{B:3c,C:7(){z.10++;z.1k=1P(z.1k/2);z.1U()}},\'E\');1E.u(-z.1k,0)}},\'E\');A.u(0,-z.1k)}I k(z.o&&z.o.17==1b){z.o(z.e.15[o])}};z.1U()};',62,244,'||||jQuery||this|function|fx|new|||return|||fn|each|||speed|if||op|left|||css||||custom|var|||||fxi|duration|complete|fxh|top|height|width|in|else|parentNode|slide|break|case|0px|px|none|style|fxReset|DropOutDirectiont|up|out|opd|wrs|wb|hb|toggle|cnt|right|down||es|cur|show|constructor|display|par|times|Function|sldd|od|om|opacity|BlindDirection|verticaly|horizontaly|no|bhight|opz|hide|di|Math|overflow|position|CloseDirection|absolute|OpenDirection|switch|fxt|DoFold|999|wr|100|fxl|oComp|fxComplete|fxw|fx2|doShake|Pulsate|relative|visible|ScrollTo|getPos|fxo|doPulsate|scroll|timer|parseInt|unfold|nodeName|Shake|60|doBounce|fx3|togglehor|block|test|browser||msie|filter|alpha|marginRight|marginBottom|marginLeft|iBounce|animate|togglever|Date|getTime|clear|marginTop|cos|PI|st|sl|hidden|step|wid|fxWrapper|auto|fold|BlindUp|BlindDown|BlindToggleVerticaly|td|BlindLeft|BlindRight|thead|tfoot|BlindToggleHorizontaly|colgroup|body|firstChild|script|frame|frameset|Fold|hasWord|UnFold|getMargins|FoldToggle|w_|random|Number|img|120|input|select|textarea|DropOutDown|form|DropInDown|table|DropToggleDown|div|DropOutUp|DropInUp|id|DropToggleUp|addClass|DropOutLeft|DropInLeft|DropToggleLeft|DropOutRight|DropInRight|DropToggleRight|Bounce|10000|wrap|listStyle|true|80|getScroll|clearInterval|null|setTimeout|CloseVerticaly|CloseHorizontaly|SwitchHorizontaly|40|SwitchVerticaly|th|header|meta|window|caption|scrollTo|setInterval|OpenVerticaly|OpenHorizontaly|SlideInUp|SlideOutUp|SlideToggleUp|SlideInDown|SlideOutDown|SlideToggleDown|tbody|SlideInLeft|SlideOutLeft|set|SlideToggleLeft|SlideInRight|SlideOutRight|SlideToggleRight|tr|SlideUp|button|iframe|object|SlideDown|SlideLeft|SlideRight|br|col|createElement|document|false'.split('|'),0,{}))
</script>
<script type="text/javascript">
		var activeMenu = false;
		$(document).ready(
		function()
		{
			$('#pull').click(hoverTrigger);
		}
		);
		hoverTrigger = function()
		{
			this.blur();
			if (activeMenu == false) {
				activeMenu = true;
				$('#shelfwrap').SlideDown(700);
			} else {
				activeMenu = false;
				$('#shelfwrap').SlideUp(700);
			}
		}
</script>

</head>

<noembed><body></noembed>

<a name="top"></a>
<div id="top"><!-- begin top -->
<div id="fix1"><!-- begin fix1 -->
<div id="fix2"><!-- begin fix2 -->
	<div id="shelfwrap" class="shelfwrap"><!-- begin shelfwrap -->
		<div id="shelf" class="shelf"><!-- begin shelf -->
			<div class="left"><!-- begin left -->
				<h3>About</h3>
				<p>"Sed ut perspiciatis unde omnis iste natus error sit voluptatem accusantium doloremque laudantium. Nemo enim ipsam voluptatem quia voluptas sit aspernatur aut odit aut fugit, sed quia consequuntur magni dolores eos qui ratione voluptatem sequi nesciunt."</p>
				<ul id="navigation">
					<li><span>Return to the frontpage</span> <a href="<$BlogURL$>" title="<$BlogTitle$>">Journal</a><br /></li>
					<li><span>About the author</span> <a href="<$BlogOwnerProfileUrl$>" title="<$BlogOwnerFullName$>">About</a><br /></li>
					<li><span>Noteworthy</span> <a href="#" onclick="$('#bottomcontent').ScrollTo(800); return false;" title="Smoothly scroll to bottom">Recents</a><br /></li>
					<li><span>Content syndication</span> <a href="<$BlogSiteFeedUrl$>" title="Syndicate this site using ATOM feed">Subscribe</a><br /></li>
					<li><span>Drop a line or two</span> <a href="mailto:me@myself.com">Contact</a><br /></li>
				</ul>
			<div id="searchbar"><!-- begin searchbar -->
				<form method="get" id="searchform" action="http://www.google.com/custom">
					<div><!-- begin misc1 -->
						<input type="text" name="q" id="search" maxlength="255" value="Weed wack" />
						<input type="hidden" name="domains" value="<$BlogURL$>" />
						<input type="hidden" name="sitesearch" value="<$BlogURL$>" />
						<span>Search Archives</span>
					</div><!-- end misc1 -->
				</form>
			</div><!-- end searchbar -->
			</div><!-- end left -->
			
			<div class="right"><!-- begin right -->
			<h3>Recent</h3>	
			<p>"Sed ut perspiciatis unde omnis iste natus error sit voluptatem accusantium doloremque laudantium, totam rem aperiam, eaque ipsa quae ab illo inventore veritatis et quasi architecto beatae vitae dicta sunt explicabo."</p>
			<ul id="recentposts">
				<BloggerPreviousItems>
					<li><a href="<$BlogItemPermalinkURL$>"><$BlogPreviousItemTitle$></a></li>
				</BloggerPreviousItems>
			</ul>
			<h3>Archives</h3>
			<ul id="archivelist">
				<BloggerArchives>
					<li><a href="<$BlogArchiveURL$>"><$BlogArchiveName$></a></li>
				</BloggerArchives>
			</ul>
			</div><!-- end right -->
	</div><!-- end shelf -->
	<div class="clear"></div>
</div><!-- end shelfwrap -->
</div><!-- end fix2 -->
</div><!-- end fix1 -->

<div id="shelfbreak"></div>

<div id="banner">
	<div id="foliage">
		<div id="pull"><a href="#">Toggle Menu</a></div>
	</div>
</div>

<MainOrArchivePage>

	<div id="content"><!-- begin content -->

<Blogger>

		<div class="post" id="post-<$BlogItemNumber$>"><!-- begin post -->
			<h2><a href="<$BlogItemPermalinkUrl$>" rel="bookmark" title="Permanent Link: <$BlogItemTitle$>"><$BlogItemTitle$></a> <span class="chrondate"><BlogDateHeader><$BlogDateHeaderDate$></BlogDateHeader> | <a href="<$BlogItemPermalinkURL$>#comments" title="Comment on <$BlogItemTitle$>"><script type="text/javascript">var a = <$BlogItemCommentCount$>; if(a == 0) {document.write('0');} else if(a == 1) {document.write('1');}else{document.write(a+'');}</script></a></span></h2>
			<div class="entry"><!-- begin entry -->
				<p><$BlogItemBody$></p>
			</div><!-- end entry -->
		</div><!-- end post -->

</Blogger>

	</div><!-- end content -->

</MainOrArchivePage>

<ItemPage>

	<div id="singlecontent"><!-- begin singlecontent -->

<Blogger>

		<div class="post" id="post-<$BlogItemNumber$>"><!-- begin post -->
			<h2><a href="<$BlogItemPermalinkUrl$>" rel="bookmark" title="Permanent Link to <$BlogItemTitle$>"><$BlogItemTitle$></a></h2>
			<div class="entrymeta"><p>Stamped: <$BlogItemDateTime$></p></div>
			<div class="entry"><!-- begin entry -->
				<p><$BlogItemBody$></p>
			</div><!-- end entry -->

<BlogItemCommentsEnabled>
		<div id="commentwrap"><!-- begin commentwrap -->
			<h3 id="respond"><a href="<$BlogItemCommentCreate$>">Leave a Reply</a></h3>
		</div><!-- end commentwrap -->
</BlogItemCommentsEnabled>

		<div class="nextprevious"><!-- begin nextprevious -->
			<div class="left"><a href="<$BlogURL$>">&laquo; Home</a></div>
			</Blogger>
			<div class="right"><BloggerPreviousItems><a href="<$BlogItemPermalinkURL$>"><$BlogPreviousItemTitle$> &raquo;</a></div><div style="display:none"></BloggerPreviousItems></div>
			<Blogger>
		</div><!-- end nextprevious -->

		</div><!-- end post -->

		<div id="commentscolumn"><!-- begin commentscolumn -->
			<h3 class="comments"><script type="text/javascript">var a = <$BlogItemCommentCount$>; if(a == 0) {document.write('no comments');} else if(a == 1) {document.write('one response');}else{document.write(a+' responses');}</script></h3>
			<div class="commentnote">You can leave your response or bookmark this post to del.icio.us by using the links below.<br /> <div style="text-align:center;"><a href="<$BlogItemCommentCreate$>" title="Leave a reply">Comment</a> | <a href="http://del.icio.us/post?url=<$BlogItemPermalinkUrl$>&amp;title=<$BlogItemTitle$>" title="Bookmark this post to del.icio.us">Bookmark</a> | <a href="#" onclick="$('#bottom').ScrollTo(800); return false;" title="Smoothly scroll to the end of the page">Go to end</a></div> </div>	

<BlogItemCommentsEnabled>

			<ul class="commentlist">

<BlogItemComments>

				<li class="alt item" id="comment-<$BlogCommentNumber$>">
					<div class="commententry"><!-- begin commententry -->
						<$BlogCommentAuthor$> says so:<br /><span style="text-transform: lowercase;"><a href="#comment-<$BlogCommentNumber$>" title="Comment Permalink"><$BlogCommentDateTime$></a> <$BlogCommentDeleteIcon$></span>
						<p><$BlogCommentBody$> <span class="right"><a href="#" onclick="$('#top').ScrollTo(800); return false;" title="Smoothly scroll to top">top</a></span></p>
					</div><!-- end commententry -->
				</li>

</BlogItemComments>

			</ul>
		</div><!-- end commentscolumn -->

</BlogItemCommentsEnabled>

		<div class="clear"></div>

</Blogger>

	</div><!-- end singlecontent -->
	
	<div class="clear"></div>

</ItemPage>

</div><!-- end top -->

<div id="footercontent"><!-- begin footercontent -->

<MainPage>
	<div id="bottomwrap"><!-- begin bottomwrap -->
		<div id="bottomcontent"><!-- begin bottomcontent -->
			<h3>Fill me with meaningful content</h3>
			<p>"Sed ut perspiciatis unde omnis iste natus error sit voluptatem accusantium doloremque laudantium, totam rem aperiam, eaque ipsa quae ab illo inventore veritatis et quasi architecto beatae vitae dicta sunt explicabo. Nemo enim ipsam voluptatem quia voluptas sit aspernatur aut odit aut fugit, sed quia consequuntur magni dolores eos qui ratione voluptatem sequi nesciunt. Neque porro quisquam est, qui dolorem ipsum quia dolor sit amet, consectetur, adipisci velit, sed quia non numquam eius modi tempora incidunt ut labore et dolore magnam aliquam quaerat voluptatem. Ut enim ad minima veniam, quis nostrum exercitationem ullam corporis suscipit laboriosam, nisi ut aliquid ex ea commodi consequatur? Quis autem vel eum iure reprehenderit qui in ea voluptate velit esse quam nihil molestiae consequatur, vel illum qui dolorem eum fugiat quo voluptas nulla pariatur?"</p>
		</div><!-- end bottomcontent -->
		<div class="clear"></div>
	</div><!-- end bottomwrap -->
</MainPage>

</div><!-- end footercontent -->
		<!--
	
			Please do not remove the credit links below, thank you.
	
		-->
<div id="bottom"><!-- begin bottom -->
<div id="footer"><!-- begin footer -->
	<p style="float: left;"><$BlogTitle$> | <a href="<$BlogSiteFeedUrl$>" title="Syndicate this site using ATOM feed">feed</a></p>
	<p style="float: right;"><a href="http://5thirtyone.com/" title="5ThirtyOne | It's not wheatgrass">5ThirtyOne</a> and <a href="http://www.bloggertemplates.org/" title="Nice and cool templates for your Blogger blog.">Blogger Templates</a> design | <a href="#" onclick="$('#top').ScrollTo(800); return false;" title="Smoothly scroll to top">Top</a></p>
</div><!-- end footer -->
</div><!-- end bottom -->
<br />
</body>

</html>
```
How can I make this work with my blog? Its the new blogger.

My Photobucket gallery (With the images) is [http://i228.photobucket.com/albums/ee303/UnabridgedExcerpts/](http://i228.photobucket.com/albums/ee303/UnabridgedExcerpts/)
All the images are uploaded under the same name they are in the file.
How do I make this work?

---

