---
title       : googleVis-Tutorial
subtitle    : Based on Gesmann and de Castillo
author      : Vivek Patil
job         : Associate Professor of Marketing
framework   : io2012        # {io2012, html5slides, shower, dzslides, ...}
highlighter : highlight.js  # {highlight.js, prettify, highlight}
hitheme     : tomorrow      # 
widgets     : [mathjax, interactive]            # {mathjax, quiz, bootstrap}
mode        : selfcontained # {standalone, draft}
---




## googleVis

* Provides an interface between Google Chart Tools and R
* Includes the beauty of Hans Rosling's motion charts (purchase of Gapminder by Google)
* https://github.com/mages/googleVis

`install.packages('googleVis')`

Who is Hans Rosling?

---

## Hans Rosling?

9 Ted Talks (through 6/2014... the highest number - next was 6)

<center>
<iframe width="640" height="360" src="http://www.youtube.com/embed/jbkSRLYSojo" frameborder="0" allowfullscreen></iframe>

--- 

## Introduction to Google Chart Tools

* Google Chart Tools provide a way to visualize data on web sites
* The API makes it easy to create interactive charts
* Browser with internet connection required to display chart
* Please read the Google [Terms of Service](https://developers.google.com/terms/) before you start

---

## Key ideas of googleVis

* Transform R data frames into [JSON](http://www.json.org/) objects with [RJSONIO](http://www.omegahat.org/RJSONIO/)


```r
library(RJSONIO)
dat <- data.frame(x=LETTERS[1:2], y=1:2)
cat(toJSON(dat)) 
```

```
## {
##  "x": [ "A", "B" ],
## "y": [ 1, 2 ] 
## }
```

* Create wrapper functions in R which generate html files with references to Google's Chart Tools API
* Display the HTML output with the R HTTP help server

---

## The googleVis concept

* Charts: *'gvis' + ChartType*
* For a motion chart we have


```r
M <- gvisMotionChart(data, idvar='id', timevar='date', 
                     options=list(), chartid)
```

* Output of googleVis is a list of list

* Display the chart by simply plotting the output: ```plot(M)```
* Plot will generate a temporary html-file and open it in a new browser window 
* Specific parts can be extracted, e.g. 
  * the chart: ```M$html$chart``` or 
  * data: ```M$html$chart["jsData"]```

---

## Types of charts 

* Histogram, Line, Line with two axes, Bar, Column, Area, Stepped Area, Combo, Scatter, Bubble, Motion, Candlestick, Pie, Gauge, Table, Organization Chart, Tree Map, Sankey, Calendar, and Time line (to check on Annotation, Annotated time line) 
* Mapping: Intensity Map, Geo Chart, Geo markers, Google map markers,Geo Map 

Run ```demo(googleVis)``` to see [examples](http://cran.r-project.org/web/packages/googleVis/vignettes/googleVis_examples.html) of all charts and read the [vignette](http://cran.r-project.org/web/packages/googleVis/vignettes/googleVis.pdf) for more details.

---

## Histogram


```r
set.seed(123)
datHist=data.frame(A=rpois(100, 20),
                   B=rpois(100, 5),
                   C=rpois(100, 50))

Hist <- gvisHistogram(datHist, options=list(
  legend="{ position: 'top', maxLines: 2 }",
  colors="['#5C3292', '#1A8763', '#871B47']",
  width=750, height=360))
plot(Hist)
```

<!-- Histogram generated in R 3.1.1 by googleVis 0.5.5 package -->
<!-- Tue Oct 14 16:33:13 2014 -->


<!-- jsHeader -->
<script type="text/javascript">
 
// jsData 
function gvisDataHistogramIDd2c615b5d3a () {
var data = new google.visualization.DataTable();
var datajson =
[
 [
 17,
8,
59 
],
[
 25,
6,
46 
],
[
 12,
4,
46 
],
[
 20,
5,
52 
],
[
 27,
2,
64 
],
[
 22,
3,
41 
],
[
 14,
4,
49 
],
[
 12,
3,
65 
],
[
 25,
7,
44 
],
[
 21,
3,
63 
],
[
 21,
7,
43 
],
[
 20,
5,
53 
],
[
 17,
6,
46 
],
[
 25,
3,
43 
],
[
 23,
6,
47 
],
[
 19,
4,
35 
],
[
 16,
6,
48 
],
[
 15,
4,
57 
],
[
 18,
10,
50 
],
[
 15,
9,
55 
],
[
 17,
6,
46 
],
[
 19,
3,
55 
],
[
 14,
3,
55 
],
[
 14,
5,
59 
],
[
 18,
4,
45 
],
[
 14,
5,
64 
],
[
 24,
7,
54 
],
[
 23,
3,
41 
],
[
 23,
4,
40 
],
[
 23,
5,
65 
],
[
 22,
8,
59 
],
[
 19,
8,
48 
],
[
 18,
8,
53 
],
[
 18,
6,
47 
],
[
 16,
9,
56 
],
[
 23,
5,
49 
],
[
 19,
5,
43 
],
[
 25,
4,
49 
],
[
 15,
4,
50 
],
[
 18,
1,
51 
],
[
 17,
5,
58 
],
[
 14,
8,
46 
],
[
 21,
0,
57 
],
[
 19,
2,
51 
],
[
 19,
3,
69 
],
[
 26,
7,
52 
],
[
 18,
6,
49 
],
[
 26,
10,
43 
],
[
 13,
5,
54 
],
[
 15,
2,
57 
],
[
 20,
6,
55 
],
[
 21,
6,
47 
],
[
 17,
3,
47 
],
[
 29,
4,
44 
],
[
 14,
3,
54 
],
[
 21,
2,
41 
],
[
 22,
4,
49 
],
[
 20,
2,
51 
],
[
 24,
3,
44 
],
[
 29,
2,
56 
],
[
 17,
6,
56 
],
[
 15,
4,
54 
],
[
 16,
2,
49 
],
[
 22,
2,
26 
],
[
 19,
8,
44 
],
[
 16,
6,
53 
],
[
 20,
7,
41 
],
[
 19,
10,
48 
],
[
 20,
2,
63 
],
[
 21,
2,
49 
],
[
 18,
7,
40 
],
[
 22,
7,
38 
],
[
 19,
1,
47 
],
[
 21,
7,
40 
],
[
 24,
6,
50 
],
[
 21,
6,
61 
],
[
 18,
5,
49 
],
[
 25,
3,
57 
],
[
 24,
1,
54 
],
[
 22,
5,
49 
],
[
 21,
5,
39 
],
[
 17,
4,
47 
],
[
 25,
5,
50 
],
[
 17,
6,
59 
],
[
 26,
2,
66 
],
[
 18,
4,
60 
],
[
 15,
7,
49 
],
[
 27,
7,
37 
],
[
 20,
3,
56 
],
[
 25,
4,
45 
],
[
 17,
7,
56 
],
[
 19,
7,
54 
],
[
 16,
4,
40 
],
[
 22,
3,
47 
],
[
 18,
6,
51 
],
[
 26,
2,
50 
],
[
 27,
1,
53 
],
[
 22,
14,
50 
],
[
 18,
1,
38 
],
[
 20,
4,
44 
] 
];
data.addColumn('number','A');
data.addColumn('number','B');
data.addColumn('number','C');
data.addRows(datajson);
return(data);
}
 
// jsDrawChart
function drawChartHistogramIDd2c615b5d3a() {
var data = gvisDataHistogramIDd2c615b5d3a();
var options = {};
options["allowHtml"] = true;
options["legend"] = { position: 'top', maxLines: 2 };
options["colors"] = ['#5C3292', '#1A8763', '#871B47'];
options["width"] =    750;
options["height"] =    360;

    var chart = new google.visualization.Histogram(
    document.getElementById('HistogramIDd2c615b5d3a')
    );
    chart.draw(data,options);
    

}
  
 
// jsDisplayChart
(function() {
var pkgs = window.__gvisPackages = window.__gvisPackages || [];
var callbacks = window.__gvisCallbacks = window.__gvisCallbacks || [];
var chartid = "corechart";
  
// Manually see if chartid is in pkgs (not all browsers support Array.indexOf)
var i, newPackage = true;
for (i = 0; newPackage && i < pkgs.length; i++) {
if (pkgs[i] === chartid)
newPackage = false;
}
if (newPackage)
  pkgs.push(chartid);
  
// Add the drawChart function to the global list of callbacks
callbacks.push(drawChartHistogramIDd2c615b5d3a);
})();
function displayChartHistogramIDd2c615b5d3a() {
  var pkgs = window.__gvisPackages = window.__gvisPackages || [];
  var callbacks = window.__gvisCallbacks = window.__gvisCallbacks || [];
  window.clearTimeout(window.__gvisLoad);
  // The timeout is set to 100 because otherwise the container div we are
  // targeting might not be part of the document yet
  window.__gvisLoad = setTimeout(function() {
  var pkgCount = pkgs.length;
  google.load("visualization", "1", { packages:pkgs, callback: function() {
  if (pkgCount != pkgs.length) {
  // Race condition where another setTimeout call snuck in after us; if
  // that call added a package, we must not shift its callback
  return;
}
while (callbacks.length > 0)
callbacks.shift()();
} });
}, 100);
}
 
// jsFooter
</script>
 
<!-- jsChart -->  
<script type="text/javascript" src="https://www.google.com/jsapi?callback=displayChartHistogramIDd2c615b5d3a"></script>
 
<!-- divChart -->
  
<div id="HistogramIDd2c615b5d3a" 
  style="width: 750; height: 360;">
</div>

---

## Line Chart


```r
df=data.frame(country=c("US", "GB", "BR"), 
              val1=c(10,13,14), 
              val2=c(23,12,32))
Line <- gvisLineChart(df,options=list(width=750, height=500))
plot(Line)
```

<!-- LineChart generated in R 3.1.1 by googleVis 0.5.5 package -->
<!-- Tue Oct 14 16:33:13 2014 -->


<!-- jsHeader -->
<script type="text/javascript">
 
// jsData 
function gvisDataLineChartIDd2c275e5976 () {
var data = new google.visualization.DataTable();
var datajson =
[
 [
 "US",
10,
23 
],
[
 "GB",
13,
12 
],
[
 "BR",
14,
32 
] 
];
data.addColumn('string','country');
data.addColumn('number','val1');
data.addColumn('number','val2');
data.addRows(datajson);
return(data);
}
 
// jsDrawChart
function drawChartLineChartIDd2c275e5976() {
var data = gvisDataLineChartIDd2c275e5976();
var options = {};
options["allowHtml"] = true;
options["width"] =    750;
options["height"] =    500;

    var chart = new google.visualization.LineChart(
    document.getElementById('LineChartIDd2c275e5976')
    );
    chart.draw(data,options);
    

}
  
 
// jsDisplayChart
(function() {
var pkgs = window.__gvisPackages = window.__gvisPackages || [];
var callbacks = window.__gvisCallbacks = window.__gvisCallbacks || [];
var chartid = "corechart";
  
// Manually see if chartid is in pkgs (not all browsers support Array.indexOf)
var i, newPackage = true;
for (i = 0; newPackage && i < pkgs.length; i++) {
if (pkgs[i] === chartid)
newPackage = false;
}
if (newPackage)
  pkgs.push(chartid);
  
// Add the drawChart function to the global list of callbacks
callbacks.push(drawChartLineChartIDd2c275e5976);
})();
function displayChartLineChartIDd2c275e5976() {
  var pkgs = window.__gvisPackages = window.__gvisPackages || [];
  var callbacks = window.__gvisCallbacks = window.__gvisCallbacks || [];
  window.clearTimeout(window.__gvisLoad);
  // The timeout is set to 100 because otherwise the container div we are
  // targeting might not be part of the document yet
  window.__gvisLoad = setTimeout(function() {
  var pkgCount = pkgs.length;
  google.load("visualization", "1", { packages:pkgs, callback: function() {
  if (pkgCount != pkgs.length) {
  // Race condition where another setTimeout call snuck in after us; if
  // that call added a package, we must not shift its callback
  return;
}
while (callbacks.length > 0)
callbacks.shift()();
} });
}, 100);
}
 
// jsFooter
</script>
 
<!-- jsChart -->  
<script type="text/javascript" src="https://www.google.com/jsapi?callback=displayChartLineChartIDd2c275e5976"></script>
 
<!-- divChart -->
  
<div id="LineChartIDd2c275e5976" 
  style="width: 750; height: 500;">
</div>

---

## Line with two axis


```r
Line2 <- gvisLineChart(df, "country", c("val1","val2"),
                       options=list(
                         series="[{targetAxisIndex: 0},
                                 {targetAxisIndex:1}]",
                         vAxes="[{title:'val1'}, {title:'val2'}]",
                         width=750, height=400
                       ))
plot(Line2)
```

<!-- LineChart generated in R 3.1.1 by googleVis 0.5.5 package -->
<!-- Tue Oct 14 16:33:13 2014 -->


<!-- jsHeader -->
<script type="text/javascript">
 
// jsData 
function gvisDataLineChartIDd2c409dfed () {
var data = new google.visualization.DataTable();
var datajson =
[
 [
 "US",
10,
23 
],
[
 "GB",
13,
12 
],
[
 "BR",
14,
32 
] 
];
data.addColumn('string','country');
data.addColumn('number','val1');
data.addColumn('number','val2');
data.addRows(datajson);
return(data);
}
 
// jsDrawChart
function drawChartLineChartIDd2c409dfed() {
var data = gvisDataLineChartIDd2c409dfed();
var options = {};
options["allowHtml"] = true;
options["series"] = [{targetAxisIndex: 0},
                                 {targetAxisIndex:1}];
options["vAxes"] = [{title:'val1'}, {title:'val2'}];
options["width"] =    750;
options["height"] =    400;

    var chart = new google.visualization.LineChart(
    document.getElementById('LineChartIDd2c409dfed')
    );
    chart.draw(data,options);
    

}
  
 
// jsDisplayChart
(function() {
var pkgs = window.__gvisPackages = window.__gvisPackages || [];
var callbacks = window.__gvisCallbacks = window.__gvisCallbacks || [];
var chartid = "corechart";
  
// Manually see if chartid is in pkgs (not all browsers support Array.indexOf)
var i, newPackage = true;
for (i = 0; newPackage && i < pkgs.length; i++) {
if (pkgs[i] === chartid)
newPackage = false;
}
if (newPackage)
  pkgs.push(chartid);
  
// Add the drawChart function to the global list of callbacks
callbacks.push(drawChartLineChartIDd2c409dfed);
})();
function displayChartLineChartIDd2c409dfed() {
  var pkgs = window.__gvisPackages = window.__gvisPackages || [];
  var callbacks = window.__gvisCallbacks = window.__gvisCallbacks || [];
  window.clearTimeout(window.__gvisLoad);
  // The timeout is set to 100 because otherwise the container div we are
  // targeting might not be part of the document yet
  window.__gvisLoad = setTimeout(function() {
  var pkgCount = pkgs.length;
  google.load("visualization", "1", { packages:pkgs, callback: function() {
  if (pkgCount != pkgs.length) {
  // Race condition where another setTimeout call snuck in after us; if
  // that call added a package, we must not shift its callback
  return;
}
while (callbacks.length > 0)
callbacks.shift()();
} });
}, 100);
}
 
// jsFooter
</script>
 
<!-- jsChart -->  
<script type="text/javascript" src="https://www.google.com/jsapi?callback=displayChartLineChartIDd2c409dfed"></script>
 
<!-- divChart -->
  
<div id="LineChartIDd2c409dfed" 
  style="width: 750; height: 400;">
</div>

---

## Customizing Lines


```r
Dashed <-  gvisLineChart(df, xvar="country", yvar=c("val1","val2"),
                        options=list(
                          series="[{color:'green', targetAxisIndex: 0, 
                          lineWidth: 1, lineDashStyle: [2, 2, 20, 2, 20, 2]}, 
                          {color: 'blue',targetAxisIndex: 1, 
                          lineWidth: 2, lineDashStyle: [4, 1]}]",
                          vAxes="[{title:'val1'}, {title:'val2'}]", width=750,height=400
                        ))
plot(Dashed)
```

<!-- LineChart generated in R 3.1.1 by googleVis 0.5.5 package -->
<!-- Tue Oct 14 16:33:13 2014 -->


<!-- jsHeader -->
<script type="text/javascript">
 
// jsData 
function gvisDataLineChartIDd2c7ca5be8 () {
var data = new google.visualization.DataTable();
var datajson =
[
 [
 "US",
10,
23 
],
[
 "GB",
13,
12 
],
[
 "BR",
14,
32 
] 
];
data.addColumn('string','country');
data.addColumn('number','val1');
data.addColumn('number','val2');
data.addRows(datajson);
return(data);
}
 
// jsDrawChart
function drawChartLineChartIDd2c7ca5be8() {
var data = gvisDataLineChartIDd2c7ca5be8();
var options = {};
options["allowHtml"] = true;
options["series"] = [{color:'green', targetAxisIndex: 0, 
                          lineWidth: 1, lineDashStyle: [2, 2, 20, 2, 20, 2]}, 
                          {color: 'blue',targetAxisIndex: 1, 
                          lineWidth: 2, lineDashStyle: [4, 1]}];
options["vAxes"] = [{title:'val1'}, {title:'val2'}];
options["width"] =    750;
options["height"] =    400;

    var chart = new google.visualization.LineChart(
    document.getElementById('LineChartIDd2c7ca5be8')
    );
    chart.draw(data,options);
    

}
  
 
// jsDisplayChart
(function() {
var pkgs = window.__gvisPackages = window.__gvisPackages || [];
var callbacks = window.__gvisCallbacks = window.__gvisCallbacks || [];
var chartid = "corechart";
  
// Manually see if chartid is in pkgs (not all browsers support Array.indexOf)
var i, newPackage = true;
for (i = 0; newPackage && i < pkgs.length; i++) {
if (pkgs[i] === chartid)
newPackage = false;
}
if (newPackage)
  pkgs.push(chartid);
  
// Add the drawChart function to the global list of callbacks
callbacks.push(drawChartLineChartIDd2c7ca5be8);
})();
function displayChartLineChartIDd2c7ca5be8() {
  var pkgs = window.__gvisPackages = window.__gvisPackages || [];
  var callbacks = window.__gvisCallbacks = window.__gvisCallbacks || [];
  window.clearTimeout(window.__gvisLoad);
  // The timeout is set to 100 because otherwise the container div we are
  // targeting might not be part of the document yet
  window.__gvisLoad = setTimeout(function() {
  var pkgCount = pkgs.length;
  google.load("visualization", "1", { packages:pkgs, callback: function() {
  if (pkgCount != pkgs.length) {
  // Race condition where another setTimeout call snuck in after us; if
  // that call added a package, we must not shift its callback
  return;
}
while (callbacks.length > 0)
callbacks.shift()();
} });
}, 100);
}
 
// jsFooter
</script>
 
<!-- jsChart -->  
<script type="text/javascript" src="https://www.google.com/jsapi?callback=displayChartLineChartIDd2c7ca5be8"></script>
 
<!-- divChart -->
  
<div id="LineChartIDd2c7ca5be8" 
  style="width: 750; height: 400;">
</div>

---

## Bar Charts


```r
Bar <- gvisBarChart(df,options=list(width=750, height=400))
plot(Bar)
```

<!-- BarChart generated in R 3.1.1 by googleVis 0.5.5 package -->
<!-- Tue Oct 14 16:33:13 2014 -->


<!-- jsHeader -->
<script type="text/javascript">
 
// jsData 
function gvisDataBarChartIDd2c38ea327f () {
var data = new google.visualization.DataTable();
var datajson =
[
 [
 "US",
10,
23 
],
[
 "GB",
13,
12 
],
[
 "BR",
14,
32 
] 
];
data.addColumn('string','country');
data.addColumn('number','val1');
data.addColumn('number','val2');
data.addRows(datajson);
return(data);
}
 
// jsDrawChart
function drawChartBarChartIDd2c38ea327f() {
var data = gvisDataBarChartIDd2c38ea327f();
var options = {};
options["allowHtml"] = true;
options["width"] =    750;
options["height"] =    400;

    var chart = new google.visualization.BarChart(
    document.getElementById('BarChartIDd2c38ea327f')
    );
    chart.draw(data,options);
    

}
  
 
// jsDisplayChart
(function() {
var pkgs = window.__gvisPackages = window.__gvisPackages || [];
var callbacks = window.__gvisCallbacks = window.__gvisCallbacks || [];
var chartid = "corechart";
  
// Manually see if chartid is in pkgs (not all browsers support Array.indexOf)
var i, newPackage = true;
for (i = 0; newPackage && i < pkgs.length; i++) {
if (pkgs[i] === chartid)
newPackage = false;
}
if (newPackage)
  pkgs.push(chartid);
  
// Add the drawChart function to the global list of callbacks
callbacks.push(drawChartBarChartIDd2c38ea327f);
})();
function displayChartBarChartIDd2c38ea327f() {
  var pkgs = window.__gvisPackages = window.__gvisPackages || [];
  var callbacks = window.__gvisCallbacks = window.__gvisCallbacks || [];
  window.clearTimeout(window.__gvisLoad);
  // The timeout is set to 100 because otherwise the container div we are
  // targeting might not be part of the document yet
  window.__gvisLoad = setTimeout(function() {
  var pkgCount = pkgs.length;
  google.load("visualization", "1", { packages:pkgs, callback: function() {
  if (pkgCount != pkgs.length) {
  // Race condition where another setTimeout call snuck in after us; if
  // that call added a package, we must not shift its callback
  return;
}
while (callbacks.length > 0)
callbacks.shift()();
} });
}, 100);
}
 
// jsFooter
</script>
 
<!-- jsChart -->  
<script type="text/javascript" src="https://www.google.com/jsapi?callback=displayChartBarChartIDd2c38ea327f"></script>
 
<!-- divChart -->
  
<div id="BarChartIDd2c38ea327f" 
  style="width: 750; height: 400;">
</div>

---

## Column Chart


```r
Column <- gvisColumnChart(df,options=list(width=750, height=400))
plot(Column)
```

<!-- ColumnChart generated in R 3.1.1 by googleVis 0.5.5 package -->
<!-- Tue Oct 14 16:33:13 2014 -->


<!-- jsHeader -->
<script type="text/javascript">
 
// jsData 
function gvisDataColumnChartIDd2c7b842d2e () {
var data = new google.visualization.DataTable();
var datajson =
[
 [
 "US",
10,
23 
],
[
 "GB",
13,
12 
],
[
 "BR",
14,
32 
] 
];
data.addColumn('string','country');
data.addColumn('number','val1');
data.addColumn('number','val2');
data.addRows(datajson);
return(data);
}
 
// jsDrawChart
function drawChartColumnChartIDd2c7b842d2e() {
var data = gvisDataColumnChartIDd2c7b842d2e();
var options = {};
options["allowHtml"] = true;
options["width"] =    750;
options["height"] =    400;

    var chart = new google.visualization.ColumnChart(
    document.getElementById('ColumnChartIDd2c7b842d2e')
    );
    chart.draw(data,options);
    

}
  
 
// jsDisplayChart
(function() {
var pkgs = window.__gvisPackages = window.__gvisPackages || [];
var callbacks = window.__gvisCallbacks = window.__gvisCallbacks || [];
var chartid = "corechart";
  
// Manually see if chartid is in pkgs (not all browsers support Array.indexOf)
var i, newPackage = true;
for (i = 0; newPackage && i < pkgs.length; i++) {
if (pkgs[i] === chartid)
newPackage = false;
}
if (newPackage)
  pkgs.push(chartid);
  
// Add the drawChart function to the global list of callbacks
callbacks.push(drawChartColumnChartIDd2c7b842d2e);
})();
function displayChartColumnChartIDd2c7b842d2e() {
  var pkgs = window.__gvisPackages = window.__gvisPackages || [];
  var callbacks = window.__gvisCallbacks = window.__gvisCallbacks || [];
  window.clearTimeout(window.__gvisLoad);
  // The timeout is set to 100 because otherwise the container div we are
  // targeting might not be part of the document yet
  window.__gvisLoad = setTimeout(function() {
  var pkgCount = pkgs.length;
  google.load("visualization", "1", { packages:pkgs, callback: function() {
  if (pkgCount != pkgs.length) {
  // Race condition where another setTimeout call snuck in after us; if
  // that call added a package, we must not shift its callback
  return;
}
while (callbacks.length > 0)
callbacks.shift()();
} });
}, 100);
}
 
// jsFooter
</script>
 
<!-- jsChart -->  
<script type="text/javascript" src="https://www.google.com/jsapi?callback=displayChartColumnChartIDd2c7b842d2e"></script>
 
<!-- divChart -->
  
<div id="ColumnChartIDd2c7b842d2e" 
  style="width: 750; height: 400;">
</div>

---

## Area Chart


```r
Area <- gvisAreaChart(df,options=list(width=750, height=400))
plot(Area)
```

<!-- AreaChart generated in R 3.1.1 by googleVis 0.5.5 package -->
<!-- Tue Oct 14 16:33:13 2014 -->


<!-- jsHeader -->
<script type="text/javascript">
 
// jsData 
function gvisDataAreaChartIDd2c4105a0d () {
var data = new google.visualization.DataTable();
var datajson =
[
 [
 "US",
10,
23 
],
[
 "GB",
13,
12 
],
[
 "BR",
14,
32 
] 
];
data.addColumn('string','country');
data.addColumn('number','val1');
data.addColumn('number','val2');
data.addRows(datajson);
return(data);
}
 
// jsDrawChart
function drawChartAreaChartIDd2c4105a0d() {
var data = gvisDataAreaChartIDd2c4105a0d();
var options = {};
options["allowHtml"] = true;
options["width"] =    750;
options["height"] =    400;

    var chart = new google.visualization.AreaChart(
    document.getElementById('AreaChartIDd2c4105a0d')
    );
    chart.draw(data,options);
    

}
  
 
// jsDisplayChart
(function() {
var pkgs = window.__gvisPackages = window.__gvisPackages || [];
var callbacks = window.__gvisCallbacks = window.__gvisCallbacks || [];
var chartid = "corechart";
  
// Manually see if chartid is in pkgs (not all browsers support Array.indexOf)
var i, newPackage = true;
for (i = 0; newPackage && i < pkgs.length; i++) {
if (pkgs[i] === chartid)
newPackage = false;
}
if (newPackage)
  pkgs.push(chartid);
  
// Add the drawChart function to the global list of callbacks
callbacks.push(drawChartAreaChartIDd2c4105a0d);
})();
function displayChartAreaChartIDd2c4105a0d() {
  var pkgs = window.__gvisPackages = window.__gvisPackages || [];
  var callbacks = window.__gvisCallbacks = window.__gvisCallbacks || [];
  window.clearTimeout(window.__gvisLoad);
  // The timeout is set to 100 because otherwise the container div we are
  // targeting might not be part of the document yet
  window.__gvisLoad = setTimeout(function() {
  var pkgCount = pkgs.length;
  google.load("visualization", "1", { packages:pkgs, callback: function() {
  if (pkgCount != pkgs.length) {
  // Race condition where another setTimeout call snuck in after us; if
  // that call added a package, we must not shift its callback
  return;
}
while (callbacks.length > 0)
callbacks.shift()();
} });
}, 100);
}
 
// jsFooter
</script>
 
<!-- jsChart -->  
<script type="text/javascript" src="https://www.google.com/jsapi?callback=displayChartAreaChartIDd2c4105a0d"></script>
 
<!-- divChart -->
  
<div id="AreaChartIDd2c4105a0d" 
  style="width: 750; height: 400;">
</div>

---

## Stepped Area Chart


```r
SteppedArea <- gvisSteppedAreaChart(df, xvar="country", 
                                    yvar=c("val1", "val2"),
                                    options=list(isStacked=TRUE, width=750,height=400))
plot(SteppedArea)
```

<!-- SteppedAreaChart generated in R 3.1.1 by googleVis 0.5.5 package -->
<!-- Tue Oct 14 16:33:13 2014 -->


<!-- jsHeader -->
<script type="text/javascript">
 
// jsData 
function gvisDataSteppedAreaChartIDd2c7de546d6 () {
var data = new google.visualization.DataTable();
var datajson =
[
 [
 "US",
10,
23 
],
[
 "GB",
13,
12 
],
[
 "BR",
14,
32 
] 
];
data.addColumn('string','country');
data.addColumn('number','val1');
data.addColumn('number','val2');
data.addRows(datajson);
return(data);
}
 
// jsDrawChart
function drawChartSteppedAreaChartIDd2c7de546d6() {
var data = gvisDataSteppedAreaChartIDd2c7de546d6();
var options = {};
options["allowHtml"] = true;
options["isStacked"] = true;
options["width"] =    750;
options["height"] =    400;

    var chart = new google.visualization.SteppedAreaChart(
    document.getElementById('SteppedAreaChartIDd2c7de546d6')
    );
    chart.draw(data,options);
    

}
  
 
// jsDisplayChart
(function() {
var pkgs = window.__gvisPackages = window.__gvisPackages || [];
var callbacks = window.__gvisCallbacks = window.__gvisCallbacks || [];
var chartid = "corechart";
  
// Manually see if chartid is in pkgs (not all browsers support Array.indexOf)
var i, newPackage = true;
for (i = 0; newPackage && i < pkgs.length; i++) {
if (pkgs[i] === chartid)
newPackage = false;
}
if (newPackage)
  pkgs.push(chartid);
  
// Add the drawChart function to the global list of callbacks
callbacks.push(drawChartSteppedAreaChartIDd2c7de546d6);
})();
function displayChartSteppedAreaChartIDd2c7de546d6() {
  var pkgs = window.__gvisPackages = window.__gvisPackages || [];
  var callbacks = window.__gvisCallbacks = window.__gvisCallbacks || [];
  window.clearTimeout(window.__gvisLoad);
  // The timeout is set to 100 because otherwise the container div we are
  // targeting might not be part of the document yet
  window.__gvisLoad = setTimeout(function() {
  var pkgCount = pkgs.length;
  google.load("visualization", "1", { packages:pkgs, callback: function() {
  if (pkgCount != pkgs.length) {
  // Race condition where another setTimeout call snuck in after us; if
  // that call added a package, we must not shift its callback
  return;
}
while (callbacks.length > 0)
callbacks.shift()();
} });
}, 100);
}
 
// jsFooter
</script>
 
<!-- jsChart -->  
<script type="text/javascript" src="https://www.google.com/jsapi?callback=displayChartSteppedAreaChartIDd2c7de546d6"></script>
 
<!-- divChart -->
  
<div id="SteppedAreaChartIDd2c7de546d6" 
  style="width: 750; height: 400;">
</div>

---

## Combo Chart


```r
Combo <- gvisComboChart(df, xvar="country",
                        yvar=c("val1", "val2"),
                        options=list(seriesType="bars",
                                     series='{1: {type:"line"}}',width=750,height=400))
plot(Combo)
```

<!-- ComboChart generated in R 3.1.1 by googleVis 0.5.5 package -->
<!-- Tue Oct 14 16:33:13 2014 -->


<!-- jsHeader -->
<script type="text/javascript">
 
// jsData 
function gvisDataComboChartIDd2c184f6524 () {
var data = new google.visualization.DataTable();
var datajson =
[
 [
 "US",
10,
23 
],
[
 "GB",
13,
12 
],
[
 "BR",
14,
32 
] 
];
data.addColumn('string','country');
data.addColumn('number','val1');
data.addColumn('number','val2');
data.addRows(datajson);
return(data);
}
 
// jsDrawChart
function drawChartComboChartIDd2c184f6524() {
var data = gvisDataComboChartIDd2c184f6524();
var options = {};
options["allowHtml"] = true;
options["seriesType"] = "bars";
options["series"] = {1: {type:"line"}};
options["width"] =    750;
options["height"] =    400;

    var chart = new google.visualization.ComboChart(
    document.getElementById('ComboChartIDd2c184f6524')
    );
    chart.draw(data,options);
    

}
  
 
// jsDisplayChart
(function() {
var pkgs = window.__gvisPackages = window.__gvisPackages || [];
var callbacks = window.__gvisCallbacks = window.__gvisCallbacks || [];
var chartid = "corechart";
  
// Manually see if chartid is in pkgs (not all browsers support Array.indexOf)
var i, newPackage = true;
for (i = 0; newPackage && i < pkgs.length; i++) {
if (pkgs[i] === chartid)
newPackage = false;
}
if (newPackage)
  pkgs.push(chartid);
  
// Add the drawChart function to the global list of callbacks
callbacks.push(drawChartComboChartIDd2c184f6524);
})();
function displayChartComboChartIDd2c184f6524() {
  var pkgs = window.__gvisPackages = window.__gvisPackages || [];
  var callbacks = window.__gvisCallbacks = window.__gvisCallbacks || [];
  window.clearTimeout(window.__gvisLoad);
  // The timeout is set to 100 because otherwise the container div we are
  // targeting might not be part of the document yet
  window.__gvisLoad = setTimeout(function() {
  var pkgCount = pkgs.length;
  google.load("visualization", "1", { packages:pkgs, callback: function() {
  if (pkgCount != pkgs.length) {
  // Race condition where another setTimeout call snuck in after us; if
  // that call added a package, we must not shift its callback
  return;
}
while (callbacks.length > 0)
callbacks.shift()();
} });
}, 100);
}
 
// jsFooter
</script>
 
<!-- jsChart -->  
<script type="text/javascript" src="https://www.google.com/jsapi?callback=displayChartComboChartIDd2c184f6524"></script>
 
<!-- divChart -->
  
<div id="ComboChartIDd2c184f6524" 
  style="width: 750; height: 400;">
</div>

---

## Scatter chart


```r
Scatter <- gvisScatterChart(women, 
                            options=list(
                              legend="none",
                              pointSize=4,lineWidth=.5, 
                              title="Women", vAxis="{title:'weight (lbs)'}",
                              hAxis="{title:'height (in)'}", 
                              width=700, height=400))
plot(Scatter)
```

<!-- ScatterChart generated in R 3.1.1 by googleVis 0.5.5 package -->
<!-- Tue Oct 14 16:33:13 2014 -->


<!-- jsHeader -->
<script type="text/javascript">
 
// jsData 
function gvisDataScatterChartIDd2c5565989 () {
var data = new google.visualization.DataTable();
var datajson =
[
 [
 58,
115 
],
[
 59,
117 
],
[
 60,
120 
],
[
 61,
123 
],
[
 62,
126 
],
[
 63,
129 
],
[
 64,
132 
],
[
 65,
135 
],
[
 66,
139 
],
[
 67,
142 
],
[
 68,
146 
],
[
 69,
150 
],
[
 70,
154 
],
[
 71,
159 
],
[
 72,
164 
] 
];
data.addColumn('number','height');
data.addColumn('number','weight');
data.addRows(datajson);
return(data);
}
 
// jsDrawChart
function drawChartScatterChartIDd2c5565989() {
var data = gvisDataScatterChartIDd2c5565989();
var options = {};
options["allowHtml"] = true;
options["legend"] = "none";
options["pointSize"] =      4;
options["lineWidth"] =    0.5;
options["title"] = "Women";
options["vAxis"] = {title:'weight (lbs)'};
options["hAxis"] = {title:'height (in)'};
options["width"] =    700;
options["height"] =    400;

    var chart = new google.visualization.ScatterChart(
    document.getElementById('ScatterChartIDd2c5565989')
    );
    chart.draw(data,options);
    

}
  
 
// jsDisplayChart
(function() {
var pkgs = window.__gvisPackages = window.__gvisPackages || [];
var callbacks = window.__gvisCallbacks = window.__gvisCallbacks || [];
var chartid = "corechart";
  
// Manually see if chartid is in pkgs (not all browsers support Array.indexOf)
var i, newPackage = true;
for (i = 0; newPackage && i < pkgs.length; i++) {
if (pkgs[i] === chartid)
newPackage = false;
}
if (newPackage)
  pkgs.push(chartid);
  
// Add the drawChart function to the global list of callbacks
callbacks.push(drawChartScatterChartIDd2c5565989);
})();
function displayChartScatterChartIDd2c5565989() {
  var pkgs = window.__gvisPackages = window.__gvisPackages || [];
  var callbacks = window.__gvisCallbacks = window.__gvisCallbacks || [];
  window.clearTimeout(window.__gvisLoad);
  // The timeout is set to 100 because otherwise the container div we are
  // targeting might not be part of the document yet
  window.__gvisLoad = setTimeout(function() {
  var pkgCount = pkgs.length;
  google.load("visualization", "1", { packages:pkgs, callback: function() {
  if (pkgCount != pkgs.length) {
  // Race condition where another setTimeout call snuck in after us; if
  // that call added a package, we must not shift its callback
  return;
}
while (callbacks.length > 0)
callbacks.shift()();
} });
}, 100);
}
 
// jsFooter
</script>
 
<!-- jsChart -->  
<script type="text/javascript" src="https://www.google.com/jsapi?callback=displayChartScatterChartIDd2c5565989"></script>
 
<!-- divChart -->
  
<div id="ScatterChartIDd2c5565989" 
  style="width: 700; height: 400;">
</div>

---

## Customizing points


```r
M <- matrix(nrow=6,ncol=6)
M[col(M)==row(M)] <- 1:6
dat <- data.frame(X=1:6, M)
SC <- gvisScatterChart(dat, 
                       options=list(
                         title="Customizing points",
                         legend="right",
                         pointSize=30,
                         series="{
                              0: { pointShape: 'circle' },
                              1: { pointShape: 'triangle' },
                              2: { pointShape: 'square' },
                              3: { pointShape: 'diamond' },
                              4: { pointShape: 'star' },
                              5: { pointShape: 'polygon' }
                              }",
                         width=750,height=400))
```

---
## Customizing points


```r
plot(SC)
```

<!-- ScatterChart generated in R 3.1.1 by googleVis 0.5.5 package -->
<!-- Tue Oct 14 16:33:13 2014 -->


<!-- jsHeader -->
<script type="text/javascript">
 
// jsData 
function gvisDataScatterChartIDd2c4cde746e () {
var data = new google.visualization.DataTable();
var datajson =
[
 [
 1,
1,
null,
null,
null,
null,
null 
],
[
 2,
null,
2,
null,
null,
null,
null 
],
[
 3,
null,
null,
3,
null,
null,
null 
],
[
 4,
null,
null,
null,
4,
null,
null 
],
[
 5,
null,
null,
null,
null,
5,
null 
],
[
 6,
null,
null,
null,
null,
null,
6 
] 
];
data.addColumn('number','X');
data.addColumn('number','X1');
data.addColumn('number','X2');
data.addColumn('number','X3');
data.addColumn('number','X4');
data.addColumn('number','X5');
data.addColumn('number','X6');
data.addRows(datajson);
return(data);
}
 
// jsDrawChart
function drawChartScatterChartIDd2c4cde746e() {
var data = gvisDataScatterChartIDd2c4cde746e();
var options = {};
options["allowHtml"] = true;
options["title"] = "Customizing points";
options["legend"] = "right";
options["pointSize"] =     30;
options["series"] = {
                              0: { pointShape: 'circle' },
                              1: { pointShape: 'triangle' },
                              2: { pointShape: 'square' },
                              3: { pointShape: 'diamond' },
                              4: { pointShape: 'star' },
                              5: { pointShape: 'polygon' }
                              };
options["width"] =    750;
options["height"] =    400;

    var chart = new google.visualization.ScatterChart(
    document.getElementById('ScatterChartIDd2c4cde746e')
    );
    chart.draw(data,options);
    

}
  
 
// jsDisplayChart
(function() {
var pkgs = window.__gvisPackages = window.__gvisPackages || [];
var callbacks = window.__gvisCallbacks = window.__gvisCallbacks || [];
var chartid = "corechart";
  
// Manually see if chartid is in pkgs (not all browsers support Array.indexOf)
var i, newPackage = true;
for (i = 0; newPackage && i < pkgs.length; i++) {
if (pkgs[i] === chartid)
newPackage = false;
}
if (newPackage)
  pkgs.push(chartid);
  
// Add the drawChart function to the global list of callbacks
callbacks.push(drawChartScatterChartIDd2c4cde746e);
})();
function displayChartScatterChartIDd2c4cde746e() {
  var pkgs = window.__gvisPackages = window.__gvisPackages || [];
  var callbacks = window.__gvisCallbacks = window.__gvisCallbacks || [];
  window.clearTimeout(window.__gvisLoad);
  // The timeout is set to 100 because otherwise the container div we are
  // targeting might not be part of the document yet
  window.__gvisLoad = setTimeout(function() {
  var pkgCount = pkgs.length;
  google.load("visualization", "1", { packages:pkgs, callback: function() {
  if (pkgCount != pkgs.length) {
  // Race condition where another setTimeout call snuck in after us; if
  // that call added a package, we must not shift its callback
  return;
}
while (callbacks.length > 0)
callbacks.shift()();
} });
}, 100);
}
 
// jsFooter
</script>
 
<!-- jsChart -->  
<script type="text/javascript" src="https://www.google.com/jsapi?callback=displayChartScatterChartIDd2c4cde746e"></script>
 
<!-- divChart -->
  
<div id="ScatterChartIDd2c4cde746e" 
  style="width: 750; height: 400;">
</div>

---

## More customizations


```r
Line3 <-  gvisLineChart(df, xvar="country", yvar=c("val1","val2"),
                        options=list(
                          title="Hello World",
                          titleTextStyle="{color:'red', 
                                           fontName:'Courier', 
                                           fontSize:16}",                         
                          backgroundColor="#D3D3D3",                          
                          vAxis="{gridlines:{color:'red', count:3}}",
                          hAxis="{title:'Country', titleTextStyle:{color:'blue'}}",
                          series="[{color:'green', targetAxisIndex: 0}, 
                                   {color: 'orange',targetAxisIndex:1}]",
                          vAxes="[{title:'val1'}, {title:'val2'}]",
                          legend="bottom",
                          curveType="function",
                          width=750,
                          height=400                         
                        ))
```

---
## More customizations


```r
plot(Line3)
```

<!-- LineChart generated in R 3.1.1 by googleVis 0.5.5 package -->
<!-- Tue Oct 14 16:33:13 2014 -->


<!-- jsHeader -->
<script type="text/javascript">
 
// jsData 
function gvisDataLineChartIDd2c11b91ad9 () {
var data = new google.visualization.DataTable();
var datajson =
[
 [
 "US",
10,
23 
],
[
 "GB",
13,
12 
],
[
 "BR",
14,
32 
] 
];
data.addColumn('string','country');
data.addColumn('number','val1');
data.addColumn('number','val2');
data.addRows(datajson);
return(data);
}
 
// jsDrawChart
function drawChartLineChartIDd2c11b91ad9() {
var data = gvisDataLineChartIDd2c11b91ad9();
var options = {};
options["allowHtml"] = true;
options["title"] = "Hello World";
options["titleTextStyle"] = {color:'red', 
                                           fontName:'Courier', 
                                           fontSize:16};
options["backgroundColor"] = "#D3D3D3";
options["vAxis"] = {gridlines:{color:'red', count:3}};
options["hAxis"] = {title:'Country', titleTextStyle:{color:'blue'}};
options["series"] = [{color:'green', targetAxisIndex: 0}, 
                                   {color: 'orange',targetAxisIndex:1}];
options["vAxes"] = [{title:'val1'}, {title:'val2'}];
options["legend"] = "bottom";
options["curveType"] = "function";
options["width"] =    750;
options["height"] =    400;

    var chart = new google.visualization.LineChart(
    document.getElementById('LineChartIDd2c11b91ad9')
    );
    chart.draw(data,options);
    

}
  
 
// jsDisplayChart
(function() {
var pkgs = window.__gvisPackages = window.__gvisPackages || [];
var callbacks = window.__gvisCallbacks = window.__gvisCallbacks || [];
var chartid = "corechart";
  
// Manually see if chartid is in pkgs (not all browsers support Array.indexOf)
var i, newPackage = true;
for (i = 0; newPackage && i < pkgs.length; i++) {
if (pkgs[i] === chartid)
newPackage = false;
}
if (newPackage)
  pkgs.push(chartid);
  
// Add the drawChart function to the global list of callbacks
callbacks.push(drawChartLineChartIDd2c11b91ad9);
})();
function displayChartLineChartIDd2c11b91ad9() {
  var pkgs = window.__gvisPackages = window.__gvisPackages || [];
  var callbacks = window.__gvisCallbacks = window.__gvisCallbacks || [];
  window.clearTimeout(window.__gvisLoad);
  // The timeout is set to 100 because otherwise the container div we are
  // targeting might not be part of the document yet
  window.__gvisLoad = setTimeout(function() {
  var pkgCount = pkgs.length;
  google.load("visualization", "1", { packages:pkgs, callback: function() {
  if (pkgCount != pkgs.length) {
  // Race condition where another setTimeout call snuck in after us; if
  // that call added a package, we must not shift its callback
  return;
}
while (callbacks.length > 0)
callbacks.shift()();
} });
}, 100);
}
 
// jsFooter
</script>
 
<!-- jsChart -->  
<script type="text/javascript" src="https://www.google.com/jsapi?callback=displayChartLineChartIDd2c11b91ad9"></script>
 
<!-- divChart -->
  
<div id="LineChartIDd2c11b91ad9" 
  style="width: 750; height: 400;">
</div>

---

## Bubble Chart


```r
Bubble <- gvisBubbleChart(Fruits, idvar="Fruit", 
                          xvar="Sales", yvar="Expenses",
                          colorvar="Year", sizevar="Profit",
                          options=list(
                            hAxis='{minValue:75, maxValue:125}',width=700,height=400))
plot(Bubble)
```

<!-- BubbleChart generated in R 3.1.1 by googleVis 0.5.5 package -->
<!-- Tue Oct 14 16:33:13 2014 -->


<!-- jsHeader -->
<script type="text/javascript">
 
// jsData 
function gvisDataBubbleChartIDd2c67ce1691 () {
var data = new google.visualization.DataTable();
var datajson =
[
 [
 "Apples",
98,
78,
"2008",
20 
],
[
 "Apples",
111,
79,
"2009",
32 
],
[
 "Apples",
89,
76,
"2010",
13 
],
[
 "Oranges",
96,
81,
"2008",
15 
],
[
 "Bananas",
85,
76,
"2008",
9 
],
[
 "Oranges",
93,
80,
"2009",
13 
],
[
 "Bananas",
94,
78,
"2009",
16 
],
[
 "Oranges",
98,
91,
"2010",
7 
],
[
 "Bananas",
81,
71,
"2010",
10 
] 
];
data.addColumn('string','Fruit');
data.addColumn('number','Sales');
data.addColumn('number','Expenses');
data.addColumn('string','Year');
data.addColumn('number','Profit');
data.addRows(datajson);
return(data);
}
 
// jsDrawChart
function drawChartBubbleChartIDd2c67ce1691() {
var data = gvisDataBubbleChartIDd2c67ce1691();
var options = {};
options["hAxis"] = {minValue:75, maxValue:125};
options["width"] =    700;
options["height"] =    400;

    var chart = new google.visualization.BubbleChart(
    document.getElementById('BubbleChartIDd2c67ce1691')
    );
    chart.draw(data,options);
    

}
  
 
// jsDisplayChart
(function() {
var pkgs = window.__gvisPackages = window.__gvisPackages || [];
var callbacks = window.__gvisCallbacks = window.__gvisCallbacks || [];
var chartid = "corechart";
  
// Manually see if chartid is in pkgs (not all browsers support Array.indexOf)
var i, newPackage = true;
for (i = 0; newPackage && i < pkgs.length; i++) {
if (pkgs[i] === chartid)
newPackage = false;
}
if (newPackage)
  pkgs.push(chartid);
  
// Add the drawChart function to the global list of callbacks
callbacks.push(drawChartBubbleChartIDd2c67ce1691);
})();
function displayChartBubbleChartIDd2c67ce1691() {
  var pkgs = window.__gvisPackages = window.__gvisPackages || [];
  var callbacks = window.__gvisCallbacks = window.__gvisCallbacks || [];
  window.clearTimeout(window.__gvisLoad);
  // The timeout is set to 100 because otherwise the container div we are
  // targeting might not be part of the document yet
  window.__gvisLoad = setTimeout(function() {
  var pkgCount = pkgs.length;
  google.load("visualization", "1", { packages:pkgs, callback: function() {
  if (pkgCount != pkgs.length) {
  // Race condition where another setTimeout call snuck in after us; if
  // that call added a package, we must not shift its callback
  return;
}
while (callbacks.length > 0)
callbacks.shift()();
} });
}, 100);
}
 
// jsFooter
</script>
 
<!-- jsChart -->  
<script type="text/javascript" src="https://www.google.com/jsapi?callback=displayChartBubbleChartIDd2c67ce1691"></script>
 
<!-- divChart -->
  
<div id="BubbleChartIDd2c67ce1691" 
  style="width: 700; height: 400;">
</div>

---

## Motion chart example


```r
M1=gvisMotionChart(Fruits, "Fruit", "Year", 
                     options=list(width=500, height=350))
print(M1,file="M1.html")
```
<iframe src="M1.html" width="600" height="600"></iframe>

---
## Candlestick chart


```r
Candle <- gvisCandlestickChart(OpenClose, 
                               options=list(legend='none', width=700,height=400))
plot(Candle)
```

<!-- CandlestickChart generated in R 3.1.1 by googleVis 0.5.5 package -->
<!-- Tue Oct 14 16:33:13 2014 -->


<!-- jsHeader -->
<script type="text/javascript">
 
// jsData 
function gvisDataCandlestickChartIDd2c33dc1b54 () {
var data = new google.visualization.DataTable();
var datajson =
[
 [
 "Mon",
20,
28,
38,
45 
],
[
 "Tues",
31,
38,
55,
66 
],
[
 "Wed",
50,
55,
77,
80 
],
[
 "Thurs",
50,
77,
66,
77 
],
[
 "Fri",
15,
66,
22,
68 
] 
];
data.addColumn('string','Weekday');
data.addColumn('number','Low');
data.addColumn('number','Open');
data.addColumn('number','Close');
data.addColumn('number','High');
data.addRows(datajson);
return(data);
}
 
// jsDrawChart
function drawChartCandlestickChartIDd2c33dc1b54() {
var data = gvisDataCandlestickChartIDd2c33dc1b54();
var options = {};
options["allowHtml"] = true;
options["legend"] = "none";
options["width"] =    700;
options["height"] =    400;

    var chart = new google.visualization.CandlestickChart(
    document.getElementById('CandlestickChartIDd2c33dc1b54')
    );
    chart.draw(data,options);
    

}
  
 
// jsDisplayChart
(function() {
var pkgs = window.__gvisPackages = window.__gvisPackages || [];
var callbacks = window.__gvisCallbacks = window.__gvisCallbacks || [];
var chartid = "corechart";
  
// Manually see if chartid is in pkgs (not all browsers support Array.indexOf)
var i, newPackage = true;
for (i = 0; newPackage && i < pkgs.length; i++) {
if (pkgs[i] === chartid)
newPackage = false;
}
if (newPackage)
  pkgs.push(chartid);
  
// Add the drawChart function to the global list of callbacks
callbacks.push(drawChartCandlestickChartIDd2c33dc1b54);
})();
function displayChartCandlestickChartIDd2c33dc1b54() {
  var pkgs = window.__gvisPackages = window.__gvisPackages || [];
  var callbacks = window.__gvisCallbacks = window.__gvisCallbacks || [];
  window.clearTimeout(window.__gvisLoad);
  // The timeout is set to 100 because otherwise the container div we are
  // targeting might not be part of the document yet
  window.__gvisLoad = setTimeout(function() {
  var pkgCount = pkgs.length;
  google.load("visualization", "1", { packages:pkgs, callback: function() {
  if (pkgCount != pkgs.length) {
  // Race condition where another setTimeout call snuck in after us; if
  // that call added a package, we must not shift its callback
  return;
}
while (callbacks.length > 0)
callbacks.shift()();
} });
}, 100);
}
 
// jsFooter
</script>
 
<!-- jsChart -->  
<script type="text/javascript" src="https://www.google.com/jsapi?callback=displayChartCandlestickChartIDd2c33dc1b54"></script>
 
<!-- divChart -->
  
<div id="CandlestickChartIDd2c33dc1b54" 
  style="width: 700; height: 400;">
</div>

---
## Pie charts (for those who insist on not changing) - Not you


```r
Pie <- gvisPieChart(CityPopularity, options=list(width=700,height=400))
plot(Pie)
```

<!-- PieChart generated in R 3.1.1 by googleVis 0.5.5 package -->
<!-- Tue Oct 14 16:33:13 2014 -->


<!-- jsHeader -->
<script type="text/javascript">
 
// jsData 
function gvisDataPieChartIDd2c368d7b4d () {
var data = new google.visualization.DataTable();
var datajson =
[
 [
 "New York",
200 
],
[
 "Boston",
300 
],
[
 "Miami",
400 
],
[
 "Chicago",
500 
],
[
 "Los Angeles",
600 
],
[
 "Houston",
700 
] 
];
data.addColumn('string','City');
data.addColumn('number','Popularity');
data.addRows(datajson);
return(data);
}
 
// jsDrawChart
function drawChartPieChartIDd2c368d7b4d() {
var data = gvisDataPieChartIDd2c368d7b4d();
var options = {};
options["allowHtml"] = true;
options["width"] =    700;
options["height"] =    400;

    var chart = new google.visualization.PieChart(
    document.getElementById('PieChartIDd2c368d7b4d')
    );
    chart.draw(data,options);
    

}
  
 
// jsDisplayChart
(function() {
var pkgs = window.__gvisPackages = window.__gvisPackages || [];
var callbacks = window.__gvisCallbacks = window.__gvisCallbacks || [];
var chartid = "corechart";
  
// Manually see if chartid is in pkgs (not all browsers support Array.indexOf)
var i, newPackage = true;
for (i = 0; newPackage && i < pkgs.length; i++) {
if (pkgs[i] === chartid)
newPackage = false;
}
if (newPackage)
  pkgs.push(chartid);
  
// Add the drawChart function to the global list of callbacks
callbacks.push(drawChartPieChartIDd2c368d7b4d);
})();
function displayChartPieChartIDd2c368d7b4d() {
  var pkgs = window.__gvisPackages = window.__gvisPackages || [];
  var callbacks = window.__gvisCallbacks = window.__gvisCallbacks || [];
  window.clearTimeout(window.__gvisLoad);
  // The timeout is set to 100 because otherwise the container div we are
  // targeting might not be part of the document yet
  window.__gvisLoad = setTimeout(function() {
  var pkgCount = pkgs.length;
  google.load("visualization", "1", { packages:pkgs, callback: function() {
  if (pkgCount != pkgs.length) {
  // Race condition where another setTimeout call snuck in after us; if
  // that call added a package, we must not shift its callback
  return;
}
while (callbacks.length > 0)
callbacks.shift()();
} });
}, 100);
}
 
// jsFooter
</script>
 
<!-- jsChart -->  
<script type="text/javascript" src="https://www.google.com/jsapi?callback=displayChartPieChartIDd2c368d7b4d"></script>
 
<!-- divChart -->
  
<div id="PieChartIDd2c368d7b4d" 
  style="width: 700; height: 400;">
</div>

---
## Gauge charts


```r
Gauge <-  gvisGauge(CityPopularity, 
                    options=list(min=0, max=800, greenFrom=500,
                                 greenTo=800, yellowFrom=300, yellowTo=500,
                                 redFrom=0, redTo=300, width=400, height=300))
print(Gauge,file="guage.html")
```
<iframe src="guage.html" width="600" height="600"></iframe>

---

## Table


```r
PopTable <- gvisTable(Population, 
                      formats=list(Population="#,###",
                                   '% of World Population'='#.#%'),
                      options=list(page='enable'))
plot(PopTable)
```

<!-- Table generated in R 3.1.1 by googleVis 0.5.5 package -->
<!-- Tue Oct 14 16:33:14 2014 -->


<!-- jsHeader -->
<script type="text/javascript">
 
// jsData 
function gvisDataTableIDd2c5e47b65 () {
var data = new google.visualization.DataTable();
var datajson =
[
 [
 "1",
"China",
1339940000,
19.5,
"<img src=\"http://upload.wikimedia.org/wikipedia/commons/thumb/f/fa/Flag_of_the_People%27s_Republic_of_China.svg/22px-Flag_of_the_People%27s_Republic_of_China.svg.png\">",
true,
new Date(2010,9,9) 
],
[
 "2",
"India",
1188650000,
17.3,
"<img src=\"http://upload.wikimedia.org/wikipedia/commons/thumb/4/41/Flag_of_India.svg/22px-Flag_of_India.svg.png\">",
true,
new Date(2010,9,9) 
],
[
 "3",
"United States",
310438000,
4.52,
"<img src=\"http://upload.wikimedia.org/wikipedia/commons/thumb/a/a4/Flag_of_the_United_States.svg/22px-Flag_of_the_United_States.svg.png\">",
true,
new Date(2010,9,9) 
],
[
 "4",
"Indonesia",
237556363,
3.46,
"<img src=\"http://upload.wikimedia.org/wikipedia/commons/thumb/9/9f/Flag_of_Indonesia.svg/22px-Flag_of_Indonesia.svg.png\">",
true,
new Date(2010,9,9) 
],
[
 "5",
"Brazil",
193626000,
2.82,
"<img src=\"http://upload.wikimedia.org/wikipedia/commons/thumb/0/05/Flag_of_Brazil.svg/22px-Flag_of_Brazil.svg.png\">",
true,
new Date(2010,9,9) 
],
[
 "6",
"Pakistan",
170745000,
2.48,
"<img src=\"http://upload.wikimedia.org/wikipedia/commons/thumb/3/32/Flag_of_Pakistan.svg/22px-Flag_of_Pakistan.svg.png\">",
true,
new Date(2010,9,9) 
],
[
 "7",
"Bangladesh",
164425000,
2.39,
"<img src=\"http://upload.wikimedia.org/wikipedia/commons/thumb/f/f9/Flag_of_Bangladesh.svg/22px-Flag_of_Bangladesh.svg.png\">",
true,
new Date(2010,9,9) 
],
[
 "8",
"Nigeria",
158259000,
2.3,
"<img src=\"http://upload.wikimedia.org/wikipedia/commons/thumb/7/79/Flag_of_Nigeria.svg/22px-Flag_of_Nigeria.svg.png\">",
true,
new Date(2010,9,9) 
],
[
 "9",
"Russia",
141927297,
2.06,
"<img src=\"http://upload.wikimedia.org/wikipedia/commons/thumb/f/f3/Flag_of_Russia.svg/22px-Flag_of_Russia.svg.png\">",
true,
new Date(2010,9,9) 
],
[
 "10",
"Japan",
127390000,
1.85,
"<img src=\"http://upload.wikimedia.org/wikipedia/commons/thumb/9/9e/Flag_of_Japan.svg/22px-Flag_of_Japan.svg.png\">",
true,
new Date(2010,9,9) 
],
[
 "11",
"Mexico",
108396211,
1.58,
"<img src=\"http://upload.wikimedia.org/wikipedia/commons/thumb/f/fc/Flag_of_Mexico.svg/22px-Flag_of_Mexico.svg.png\">",
true,
new Date(2010,9,9) 
],
[
 "12",
"Philippines",
94013200,
1.37,
"<img src=\"http://upload.wikimedia.org/wikipedia/commons/thumb/9/99/Flag_of_the_Philippines.svg/22px-Flag_of_the_Philippines.svg.png\">",
true,
new Date(2010,9,9) 
],
[
 "13",
"Vietnam",
85846997,
1.25,
"<img src=\"http://upload.wikimedia.org/wikipedia/commons/thumb/2/21/Flag_of_Vietnam.svg/22px-Flag_of_Vietnam.svg.png\">",
true,
new Date(2010,9,9) 
],
[
 "14",
"Ethiopia",
84976000,
1.24,
"<img src=\"http://upload.wikimedia.org/wikipedia/commons/thumb/7/71/Flag_of_Ethiopia.svg/22px-Flag_of_Ethiopia.svg.png\">",
true,
new Date(2010,9,9) 
],
[
 "15",
"Germany",
81802257,
1.19,
"<img src=\"http://upload.wikimedia.org/wikipedia/commons/thumb/b/ba/Flag_of_Germany.svg/22px-Flag_of_Germany.svg.png\">",
true,
new Date(2010,9,9) 
],
[
 "16",
"Egypt",
79135000,
1.15,
"<img src=\"http://upload.wikimedia.org/wikipedia/commons/thumb/f/fe/Flag_of_Egypt.svg/22px-Flag_of_Egypt.svg.png\">",
true,
new Date(2010,9,9) 
],
[
 "17",
"Iran",
75078000,
1.09,
"<img src=\"http://upload.wikimedia.org/wikipedia/commons/thumb/c/ca/Flag_of_Iran.svg/22px-Flag_of_Iran.svg.png\">",
true,
new Date(2010,9,9) 
],
[
 "18",
"Turkey",
72561312,
1.06,
"<img src=\"http://upload.wikimedia.org/wikipedia/commons/thumb/b/b4/Flag_of_Turkey.svg/22px-Flag_of_Turkey.svg.png\">",
true,
new Date(2010,9,9) 
],
[
 "19",
"Dem. Rep. of Congo",
67827000,
0.99,
"<img src=\"http://upload.wikimedia.org/wikipedia/commons/thumb/6/6f/Flag_of_the_Democratic_Republic_of_the_Congo.svg/22px-Flag_of_the_Democratic_Republic_of_the_Congo.svg.png\">",
true,
new Date(2010,9,9) 
],
[
 "20",
"Thailand",
67070000,
1,
"<img src=\"http://upload.wikimedia.org/wikipedia/commons/thumb/a/a9/Flag_of_Thailand.svg/22px-Flag_of_Thailand.svg.png\">",
true,
new Date(2010,9,9) 
],
[
 "21",
"France",
65447374,
0.95,
"<img src=\"http://upload.wikimedia.org/wikipedia/commons/thumb/c/c3/Flag_of_France.svg/22px-Flag_of_France.svg.png\">",
true,
new Date(2010,9,9) 
],
[
 "22",
"United Kingdom",
62008049,
0.9,
"<img src=\"http://upload.wikimedia.org/wikipedia/commons/thumb/a/ae/Flag_of_the_United_Kingdom.svg/22px-Flag_of_the_United_Kingdom.svg.png\">",
true,
new Date(2010,9,9) 
],
[
 "23",
"Italy",
60402499,
0.88,
"<img src=\"http://upload.wikimedia.org/wikipedia/commons/thumb/0/03/Flag_of_Italy.svg/22px-Flag_of_Italy.svg.png\">",
true,
new Date(2010,9,9) 
],
[
 "24",
"Myanmar",
50496000,
0.73,
"<img src=\"http://upload.wikimedia.org/wikipedia/commons/thumb/8/8c/Flag_of_Myanmar.svg/22px-Flag_of_Myanmar.svg.png\">",
true,
new Date(2010,9,9) 
],
[
 "25",
"South Africa",
49991300,
0.73,
"<img src=\"http://upload.wikimedia.org/wikipedia/commons/thumb/a/af/Flag_of_South_Africa.svg/22px-Flag_of_South_Africa.svg.png\">",
true,
new Date(2010,9,9) 
],
[
 "26",
"South Korea",
49773145,
0.72,
"<img src=\"http://upload.wikimedia.org/wikipedia/commons/thumb/0/09/Flag_of_South_Korea.svg/22px-Flag_of_South_Korea.svg.png\">",
true,
new Date(2010,9,9) 
],
[
 "27",
"Spain",
46072834,
0.67,
"<img src=\"http://upload.wikimedia.org/wikipedia/commons/thumb/9/9a/Flag_of_Spain.svg/22px-Flag_of_Spain.svg.png\">",
true,
new Date(2010,9,9) 
],
[
 "28",
"Ukraine",
45871738,
0.67,
"<img src=\"http://upload.wikimedia.org/wikipedia/commons/thumb/4/49/Flag_of_Ukraine.svg/22px-Flag_of_Ukraine.svg.png\">",
true,
new Date(2010,9,9) 
],
[
 "29",
"Colombia",
45655000,
0.66,
"<img src=\"http://upload.wikimedia.org/wikipedia/commons/thumb/2/21/Flag_of_Colombia.svg/22px-Flag_of_Colombia.svg.png\">",
true,
new Date(2010,9,9) 
],
[
 "30",
"Tanzania",
45040000,
0.66,
"<img src=\"http://upload.wikimedia.org/wikipedia/commons/thumb/3/38/Flag_of_Tanzania.svg/22px-Flag_of_Tanzania.svg.png\">",
true,
new Date(2010,9,9) 
],
[
 "31",
"Sudan",
43192000,
0.63,
"<img src=\"http://upload.wikimedia.org/wikipedia/commons/thumb/0/01/Flag_of_Sudan.svg/22px-Flag_of_Sudan.svg.png\">",
true,
new Date(2010,9,9) 
],
[
 "32",
"Argentina",
40518951,
0.59,
"<img src=\"http://upload.wikimedia.org/wikipedia/commons/thumb/1/1a/Flag_of_Argentina.svg/22px-Flag_of_Argentina.svg.png\">",
true,
new Date(2010,9,9) 
],
[
 "33",
"Kenya",
38610097,
0.56,
"<img src=\"http://upload.wikimedia.org/wikipedia/commons/thumb/4/49/Flag_of_Kenya.svg/22px-Flag_of_Kenya.svg.png\">",
true,
new Date(2010,9,9) 
],
[
 "34",
"Poland",
38167329,
0.56,
"<img src=\"http://upload.wikimedia.org/wikipedia/commons/thumb/1/12/Flag_of_Poland.svg/22px-Flag_of_Poland.svg.png\">",
true,
new Date(2010,9,9) 
],
[
 "35",
"Algeria",
35423000,
0.52,
"<img src=\"http://upload.wikimedia.org/wikipedia/commons/thumb/7/77/Flag_of_Algeria.svg/22px-Flag_of_Algeria.svg.png\">",
true,
new Date(2010,9,9) 
],
[
 "36",
"Canada",
34272000,
0.5,
"<img src=\"http://upload.wikimedia.org/wikipedia/commons/thumb/c/cf/Flag_of_Canada.svg/22px-Flag_of_Canada.svg.png\">",
true,
new Date(2010,9,9) 
],
[
 "37",
"Uganda",
33796000,
0.49,
"<img src=\"http://upload.wikimedia.org/wikipedia/commons/thumb/4/4e/Flag_of_Uganda.svg/22px-Flag_of_Uganda.svg.png\">",
true,
new Date(2010,9,9) 
],
[
 "38",
"Morocco",
31944000,
0.46,
"<img src=\"http://upload.wikimedia.org/wikipedia/commons/thumb/2/2c/Flag_of_Morocco.svg/22px-Flag_of_Morocco.svg.png\">",
true,
new Date(2010,9,9) 
],
[
 "39",
"Iraq",
31467000,
0.46,
"<img src=\"http://upload.wikimedia.org/wikipedia/commons/thumb/f/f6/Flag_of_Iraq.svg/22px-Flag_of_Iraq.svg.png\">",
true,
new Date(2010,9,9) 
],
[
 "40",
"Nepal",
29853000,
0.43,
"<img src=\"http://upload.wikimedia.org/wikipedia/commons/thumb/9/9b/Flag_of_Nepal.svg/16px-Flag_of_Nepal.svg.png\">",
true,
new Date(2010,9,9) 
],
[
 "41",
"Peru",
29461933,
0.43,
"<img src=\"http://upload.wikimedia.org/wikipedia/commons/thumb/c/cf/Flag_of_Peru.svg/22px-Flag_of_Peru.svg.png\">",
true,
new Date(2010,9,9) 
],
[
 "42",
"Afghanistan",
29117000,
0.42,
"<img src=\"http://upload.wikimedia.org/wikipedia/commons/thumb/9/9a/Flag_of_Afghanistan.svg/22px-Flag_of_Afghanistan.svg.png\">",
true,
new Date(2010,9,9) 
],
[
 "43",
"Venezuela",
28958000,
0.42,
"<img src=\"http://upload.wikimedia.org/wikipedia/commons/thumb/0/06/Flag_of_Venezuela.svg/22px-Flag_of_Venezuela.svg.png\">",
true,
new Date(2010,9,9) 
],
[
 "44",
"Malaysia",
28250500,
0.41,
"<img src=\"http://upload.wikimedia.org/wikipedia/commons/thumb/6/66/Flag_of_Malaysia.svg/22px-Flag_of_Malaysia.svg.png\">",
true,
new Date(2010,9,9) 
],
[
 "45",
"Uzbekistan",
27794000,
0.4,
"<img src=\"http://upload.wikimedia.org/wikipedia/commons/thumb/8/84/Flag_of_Uzbekistan.svg/22px-Flag_of_Uzbekistan.svg.png\">",
true,
new Date(2010,9,9) 
],
[
 "46",
"Saudi Arabia",
27136977,
0.39,
"<img src=\"http://upload.wikimedia.org/wikipedia/commons/thumb/0/0d/Flag_of_Saudi_Arabia.svg/22px-Flag_of_Saudi_Arabia.svg.png\">",
true,
new Date(2010,9,9) 
],
[
 "47",
"Ghana",
24333000,
0.35,
"<img src=\"http://upload.wikimedia.org/wikipedia/commons/thumb/1/19/Flag_of_Ghana.svg/22px-Flag_of_Ghana.svg.png\">",
true,
new Date(2010,9,9) 
],
[
 "48",
"Yemen",
24256000,
0.35,
"<img src=\"http://upload.wikimedia.org/wikipedia/commons/thumb/8/89/Flag_of_Yemen.svg/22px-Flag_of_Yemen.svg.png\">",
true,
new Date(2010,9,9) 
],
[
 "49",
"North Korea",
23991000,
0.35,
"<img src=\"http://upload.wikimedia.org/wikipedia/commons/thumb/5/51/Flag_of_North_Korea.svg/22px-Flag_of_North_Korea.svg.png\">",
true,
new Date(2010,9,9) 
],
[
 "50",
"Mozambique",
23406000,
0.34,
"<img src=\"http://upload.wikimedia.org/wikipedia/commons/thumb/d/d0/Flag_of_Mozambique.svg/22px-Flag_of_Mozambique.svg.png\">",
true,
new Date(2010,9,9) 
],
[
 "52",
"Syria",
22505000,
0.33,
"<img src=\"http://upload.wikimedia.org/wikipedia/commons/thumb/5/53/Flag_of_Syria.svg/22px-Flag_of_Syria.svg.png\">",
true,
new Date(2010,9,9) 
],
[
 "53",
"Australia",
22483305,
0.33,
"<img src=\"http://upload.wikimedia.org/wikipedia/commons/thumb/b/b9/Flag_of_Australia.svg/22px-Flag_of_Australia.svg.png\">",
true,
new Date(2010,9,9) 
],
[
 "54",
"Cote d'Ivoire",
21571000,
0.31,
"<img src=\"http://upload.wikimedia.org/wikipedia/commons/thumb/8/86/Flag_of_Cote_d%27Ivoire.svg/22px-Flag_of_Cote_d%27Ivoire.svg.png\">",
true,
new Date(2010,9,9) 
],
[
 "55",
"Romania",
21466174,
0.31,
"<img src=\"http://upload.wikimedia.org/wikipedia/commons/thumb/7/73/Flag_of_Romania.svg/22px-Flag_of_Romania.svg.png\">",
true,
new Date(2010,9,9) 
],
[
 "56",
"Sri Lanka",
20410000,
0.3,
"<img src=\"http://upload.wikimedia.org/wikipedia/commons/thumb/1/11/Flag_of_Sri_Lanka.svg/22px-Flag_of_Sri_Lanka.svg.png\">",
true,
new Date(2010,9,9) 
],
[
 "57",
"Madagascar",
20146000,
0.29,
"<img src=\"http://upload.wikimedia.org/wikipedia/commons/thumb/b/bc/Flag_of_Madagascar.svg/22px-Flag_of_Madagascar.svg.png\">",
true,
new Date(2010,9,9) 
],
[
 "58",
"Cameroon",
19958000,
0.29,
"<img src=\"http://upload.wikimedia.org/wikipedia/commons/thumb/4/4f/Flag_of_Cameroon.svg/22px-Flag_of_Cameroon.svg.png\">",
true,
new Date(2010,9,9) 
],
[
 "59",
"Angola",
18993000,
0.28,
"<img src=\"http://upload.wikimedia.org/wikipedia/commons/thumb/9/9d/Flag_of_Angola.svg/22px-Flag_of_Angola.svg.png\">",
true,
new Date(2010,9,9) 
],
[
 "60",
"Chile",
17140000,
0.25,
"<img src=\"http://upload.wikimedia.org/wikipedia/commons/thumb/7/78/Flag_of_Chile.svg/22px-Flag_of_Chile.svg.png\">",
true,
new Date(2010,9,9) 
],
[
 "61",
"Netherlands",
16619500,
0.242,
"<img src=\"http://upload.wikimedia.org/wikipedia/commons/thumb/2/20/Flag_of_the_Netherlands.svg/22px-Flag_of_the_Netherlands.svg.png\">",
true,
new Date(2010,9,9) 
],
[
 "62",
"Burkina Faso",
16287000,
0.24,
"<img src=\"http://upload.wikimedia.org/wikipedia/commons/thumb/3/31/Flag_of_Burkina_Faso.svg/22px-Flag_of_Burkina_Faso.svg.png\">",
true,
new Date(2010,9,9) 
],
[
 "63",
"Kazakhstan",
16197000,
0.24,
"<img src=\"http://upload.wikimedia.org/wikipedia/commons/thumb/d/d3/Flag_of_Kazakhstan.svg/22px-Flag_of_Kazakhstan.svg.png\">",
true,
new Date(2010,9,9) 
],
[
 "64",
"Niger",
15891000,
0.23,
"<img src=\"http://upload.wikimedia.org/wikipedia/commons/thumb/f/f4/Flag_of_Niger.svg/22px-Flag_of_Niger.svg.png\">",
true,
new Date(2010,9,9) 
],
[
 "65",
"Malawi",
15692000,
0.23,
"<img src=\"http://upload.wikimedia.org/wikipedia/commons/thumb/d/d1/Flag_of_Malawi.svg/22px-Flag_of_Malawi.svg.png\">",
true,
new Date(2010,9,9) 
],
[
 "66",
"Mali",
14517176,
0.21,
"<img src=\"http://upload.wikimedia.org/wikipedia/commons/thumb/9/92/Flag_of_Mali.svg/22px-Flag_of_Mali.svg.png\">",
true,
new Date(2010,9,9) 
],
[
 "67",
"Guatemala",
14377000,
0.21,
"<img src=\"http://upload.wikimedia.org/wikipedia/commons/thumb/e/ec/Flag_of_Guatemala.svg/22px-Flag_of_Guatemala.svg.png\">",
true,
new Date(2010,9,9) 
],
[
 "68",
"Ecuador",
14259000,
0.21,
"<img src=\"http://upload.wikimedia.org/wikipedia/commons/thumb/e/e8/Flag_of_Ecuador.svg/22px-Flag_of_Ecuador.svg.png\">",
true,
new Date(2010,9,9) 
],
[
 "69",
"Cambodia",
13395682,
0.19,
"<img src=\"http://upload.wikimedia.org/wikipedia/commons/thumb/8/83/Flag_of_Cambodia.svg/22px-Flag_of_Cambodia.svg.png\">",
true,
new Date(2010,9,9) 
],
[
 "70",
"Zambia",
13257000,
0.19,
"<img src=\"http://upload.wikimedia.org/wikipedia/commons/thumb/0/06/Flag_of_Zambia.svg/22px-Flag_of_Zambia.svg.png\">",
true,
new Date(2010,9,9) 
],
[
 "71",
"Senegal",
12861000,
0.19,
"<img src=\"http://upload.wikimedia.org/wikipedia/commons/thumb/f/fd/Flag_of_Senegal.svg/22px-Flag_of_Senegal.svg.png\">",
true,
new Date(2010,9,9) 
],
[
 "72",
"Zimbabwe",
12644000,
0.18,
"<img src=\"http://upload.wikimedia.org/wikipedia/commons/thumb/6/6a/Flag_of_Zimbabwe.svg/22px-Flag_of_Zimbabwe.svg.png\">",
true,
new Date(2010,9,9) 
],
[
 "73",
"Chad",
11506000,
0.17,
"<img src=\"http://upload.wikimedia.org/wikipedia/commons/thumb/4/4b/Flag_of_Chad.svg/22px-Flag_of_Chad.svg.png\">",
true,
new Date(2010,9,9) 
],
[
 "74",
"Greece",
11306183,
0.16,
"<img src=\"http://upload.wikimedia.org/wikipedia/commons/thumb/5/5c/Flag_of_Greece.svg/22px-Flag_of_Greece.svg.png\">",
true,
new Date(2010,9,9) 
],
[
 "75",
"Cuba",
11204000,
0.16,
"<img src=\"http://upload.wikimedia.org/wikipedia/commons/thumb/b/bd/Flag_of_Cuba.svg/22px-Flag_of_Cuba.svg.png\">",
true,
new Date(2010,9,9) 
],
[
 "76",
"Belgium",
10827519,
0.16,
"<img src=\"http://upload.wikimedia.org/wikipedia/commons/thumb/9/92/Flag_of_Belgium_%28civil%29.svg/22px-Flag_of_Belgium_%28civil%29.svg.png\">",
true,
new Date(2010,9,9) 
],
[
 "77",
"Portugal",
10636888,
0.15,
"<img src=\"http://upload.wikimedia.org/wikipedia/commons/thumb/5/5c/Flag_of_Portugal.svg/22px-Flag_of_Portugal.svg.png\">",
true,
new Date(2010,9,9) 
],
[
 "78",
"Czech Republic",
10512397,
0.15,
"<img src=\"http://upload.wikimedia.org/wikipedia/commons/thumb/c/cb/Flag_of_the_Czech_Republic.svg/22px-Flag_of_the_Czech_Republic.svg.png\">",
true,
new Date(2010,9,9) 
],
[
 "79",
"Tunisia",
10432500,
0.15,
"<img src=\"http://upload.wikimedia.org/wikipedia/commons/thumb/c/ce/Flag_of_Tunisia.svg/22px-Flag_of_Tunisia.svg.png\">",
true,
new Date(2010,9,9) 
],
[
 "80",
"Guinea",
10324000,
0.15,
"<img src=\"http://upload.wikimedia.org/wikipedia/commons/thumb/e/ed/Flag_of_Guinea.svg/22px-Flag_of_Guinea.svg.png\">",
true,
new Date(2010,9,9) 
],
[
 "81",
"Rwanda",
10277000,
0.15,
"<img src=\"http://upload.wikimedia.org/wikipedia/commons/thumb/1/17/Flag_of_Rwanda.svg/22px-Flag_of_Rwanda.svg.png\">",
true,
new Date(2010,9,9) 
],
[
 "82",
"Dominican Republic",
10225000,
0.15,
"<img src=\"http://upload.wikimedia.org/wikipedia/commons/thumb/9/9f/Flag_of_the_Dominican_Republic.svg/22px-Flag_of_the_Dominican_Republic.svg.png\">",
true,
new Date(2010,9,9) 
],
[
 "83",
"Haiti",
10188000,
0.15,
"<img src=\"http://upload.wikimedia.org/wikipedia/commons/thumb/5/56/Flag_of_Haiti.svg/22px-Flag_of_Haiti.svg.png\">",
true,
new Date(2010,9,9) 
],
[
 "84",
"Bolivia",
10031000,
0.15,
"<img src=\"http://upload.wikimedia.org/wikipedia/commons/thumb/4/48/Flag_of_Bolivia.svg/22px-Flag_of_Bolivia.svg.png\">",
true,
new Date(2010,9,9) 
],
[
 "85",
"Hungary",
10013628,
0.15,
"<img src=\"http://upload.wikimedia.org/wikipedia/commons/thumb/c/c1/Flag_of_Hungary.svg/22px-Flag_of_Hungary.svg.png\">",
true,
new Date(2010,9,9) 
],
[
 "86",
"Serbia",
9856000,
0.14,
"<img src=\"http://upload.wikimedia.org/wikipedia/commons/thumb/f/ff/Flag_of_Serbia.svg/22px-Flag_of_Serbia.svg.png\">",
true,
new Date(2010,9,9) 
],
[
 "87",
"Belarus",
9467700,
0.14,
"<img src=\"http://upload.wikimedia.org/wikipedia/commons/thumb/8/85/Flag_of_Belarus.svg/22px-Flag_of_Belarus.svg.png\">",
true,
new Date(2010,9,9) 
],
[
 "88",
"Sweden",
9393648,
0.14,
"<img src=\"http://upload.wikimedia.org/wikipedia/commons/thumb/4/4c/Flag_of_Sweden.svg/22px-Flag_of_Sweden.svg.png\">",
true,
new Date(2010,9,9) 
],
[
 "89",
"Somalia",
9359000,
0.14,
"<img src=\"http://upload.wikimedia.org/wikipedia/commons/thumb/a/a0/Flag_of_Somalia.svg/22px-Flag_of_Somalia.svg.png\">",
true,
new Date(2010,9,9) 
],
[
 "90",
"Benin",
9212000,
0.13,
"<img src=\"http://upload.wikimedia.org/wikipedia/commons/thumb/0/0a/Flag_of_Benin.svg/22px-Flag_of_Benin.svg.png\">",
true,
new Date(2010,9,9) 
],
[
 "91",
"Azerbaijan",
8997400,
0.13,
"<img src=\"http://upload.wikimedia.org/wikipedia/commons/thumb/d/dd/Flag_of_Azerbaijan.svg/22px-Flag_of_Azerbaijan.svg.png\">",
true,
new Date(2010,9,9) 
],
[
 "92",
"Burundi",
8519000,
0.12,
"<img src=\"http://upload.wikimedia.org/wikipedia/commons/thumb/5/50/Flag_of_Burundi.svg/22px-Flag_of_Burundi.svg.png\">",
true,
new Date(2010,9,9) 
],
[
 "93",
"Austria",
8372930,
0.12,
"<img src=\"http://upload.wikimedia.org/wikipedia/commons/thumb/4/41/Flag_of_Austria.svg/22px-Flag_of_Austria.svg.png\">",
true,
new Date(2010,9,9) 
],
[
 "94",
"Switzerland",
7782900,
0.11,
"<img src=\"http://upload.wikimedia.org/wikipedia/commons/thumb/f/f3/Flag_of_Switzerland.svg/20px-Flag_of_Switzerland.svg.png\">",
true,
new Date(2010,9,9) 
],
[
 "95",
"Israel",
7640800,
0.11,
"<img src=\"http://upload.wikimedia.org/wikipedia/commons/thumb/d/d4/Flag_of_Israel.svg/22px-Flag_of_Israel.svg.png\">",
true,
new Date(2010,9,9) 
],
[
 "96",
"Honduras",
7616000,
0.11,
"<img src=\"http://upload.wikimedia.org/wikipedia/commons/thumb/8/82/Flag_of_Honduras.svg/22px-Flag_of_Honduras.svg.png\">",
true,
new Date(2010,9,9) 
],
[
 "97",
"Bulgaria",
7576751,
0.11,
"<img src=\"http://upload.wikimedia.org/wikipedia/commons/thumb/9/9a/Flag_of_Bulgaria.svg/22px-Flag_of_Bulgaria.svg.png\">",
true,
new Date(2010,9,9) 
],
[
 "98",
"Tajikistan",
7075000,
0.103,
"<img src=\"http://upload.wikimedia.org/wikipedia/commons/thumb/d/d0/Flag_of_Tajikistan.svg/22px-Flag_of_Tajikistan.svg.png\">",
true,
new Date(2010,9,9) 
],
[
 "100",
"Papua New Guinea",
6888000,
0.1,
"<img src=\"http://upload.wikimedia.org/wikipedia/commons/thumb/e/e3/Flag_of_Papua_New_Guinea.svg/22px-Flag_of_Papua_New_Guinea.svg.png\">",
true,
new Date(2010,9,9) 
],
[
 "101",
"Togo",
6780000,
0.099,
"<img src=\"http://upload.wikimedia.org/wikipedia/commons/thumb/6/68/Flag_of_Togo.svg/22px-Flag_of_Togo.svg.png\">",
true,
new Date(2010,9,9) 
],
[
 "102",
"Libya",
6546000,
0.095,
"<img src=\"http://upload.wikimedia.org/wikipedia/commons/thumb/0/05/Flag_of_Libya.svg/22px-Flag_of_Libya.svg.png\">",
true,
new Date(2010,9,9) 
],
[
 "103",
"Jordan",
6472000,
0.094,
"<img src=\"http://upload.wikimedia.org/wikipedia/commons/thumb/c/c0/Flag_of_Jordan.svg/22px-Flag_of_Jordan.svg.png\">",
true,
new Date(2010,9,9) 
],
[
 "104",
"Paraguay",
6460000,
0.094,
"<img src=\"http://upload.wikimedia.org/wikipedia/commons/thumb/2/27/Flag_of_Paraguay.svg/22px-Flag_of_Paraguay.svg.png\">",
true,
new Date(2010,9,9) 
],
[
 "105",
"Laos",
6436000,
0.094,
"<img src=\"http://upload.wikimedia.org/wikipedia/commons/thumb/5/56/Flag_of_Laos.svg/22px-Flag_of_Laos.svg.png\">",
true,
new Date(2010,9,9) 
],
[
 "106",
"El Salvador",
6194000,
0.09,
"<img src=\"http://upload.wikimedia.org/wikipedia/commons/thumb/3/34/Flag_of_El_Salvador.svg/22px-Flag_of_El_Salvador.svg.png\">",
true,
new Date(2010,9,9) 
],
[
 "107",
"Sierra Leone",
5836000,
0.085,
"<img src=\"http://upload.wikimedia.org/wikipedia/commons/thumb/1/17/Flag_of_Sierra_Leone.svg/22px-Flag_of_Sierra_Leone.svg.png\">",
true,
new Date(2010,9,9) 
],
[
 "108",
"Nicaragua",
5822000,
0.085,
"<img src=\"http://upload.wikimedia.org/wikipedia/commons/thumb/1/19/Flag_of_Nicaragua.svg/22px-Flag_of_Nicaragua.svg.png\">",
true,
new Date(2010,9,9) 
],
[
 "109",
"Kyrgyzstan",
5550000,
0.081,
"<img src=\"http://upload.wikimedia.org/wikipedia/commons/thumb/c/c7/Flag_of_Kyrgyzstan.svg/22px-Flag_of_Kyrgyzstan.svg.png\">",
true,
new Date(2010,9,9) 
],
[
 "110",
"Denmark",
5543819,
0.08,
"<img src=\"http://upload.wikimedia.org/wikipedia/commons/thumb/9/9c/Flag_of_Denmark.svg/22px-Flag_of_Denmark.svg.png\">",
true,
new Date(2010,9,9) 
],
[
 "111",
"Slovakia",
5429763,
0.079,
"<img src=\"http://upload.wikimedia.org/wikipedia/commons/thumb/e/e6/Flag_of_Slovakia.svg/22px-Flag_of_Slovakia.svg.png\">",
true,
new Date(2010,9,9) 
],
[
 "112",
"Finland",
5370000,
0.078,
"<img src=\"http://upload.wikimedia.org/wikipedia/commons/thumb/b/bc/Flag_of_Finland.svg/22px-Flag_of_Finland.svg.png\">",
true,
new Date(2010,9,9) 
],
[
 "113",
"Eritrea",
5224000,
0.076,
"<img src=\"http://upload.wikimedia.org/wikipedia/commons/thumb/2/29/Flag_of_Eritrea.svg/22px-Flag_of_Eritrea.svg.png\">",
true,
new Date(2010,9,9) 
],
[
 "114",
"Turkmenistan",
5177000,
0.075,
"<img src=\"http://upload.wikimedia.org/wikipedia/commons/thumb/1/1b/Flag_of_Turkmenistan.svg/22px-Flag_of_Turkmenistan.svg.png\">",
true,
new Date(2010,9,9) 
],
[
 "115",
"Singapore",
5076700,
0.074,
"<img src=\"http://upload.wikimedia.org/wikipedia/commons/thumb/4/48/Flag_of_Singapore.svg/22px-Flag_of_Singapore.svg.png\">",
true,
new Date(2010,9,9) 
],
[
 "116",
"Norway",
4906500,
0.071,
"<img src=\"http://upload.wikimedia.org/wikipedia/commons/thumb/d/d9/Flag_of_Norway.svg/22px-Flag_of_Norway.svg.png\">",
true,
new Date(2010,9,9) 
],
[
 "117",
"United Arab Emirates",
4707000,
0.068,
"<img src=\"http://upload.wikimedia.org/wikipedia/commons/thumb/c/cb/Flag_of_the_United_Arab_Emirates.svg/22px-Flag_of_the_United_Arab_Emirates.svg.png\">",
true,
new Date(2010,9,9) 
],
[
 "118",
"Costa Rica",
4640000,
0.068,
"<img src=\"http://upload.wikimedia.org/wikipedia/commons/thumb/f/f2/Flag_of_Costa_Rica.svg/22px-Flag_of_Costa_Rica.svg.png\">",
true,
new Date(2010,9,9) 
],
[
 "119",
"Central African Republic",
4506000,
0.066,
"<img src=\"http://upload.wikimedia.org/wikipedia/commons/thumb/6/6f/Flag_of_the_Central_African_Republic.svg/22px-Flag_of_the_Central_African_Republic.svg.png\">",
true,
new Date(2010,9,9) 
],
[
 "120",
"Ireland",
4470700,
0.064,
"<img src=\"http://upload.wikimedia.org/wikipedia/commons/thumb/4/45/Flag_of_Ireland.svg/22px-Flag_of_Ireland.svg.png\">",
true,
new Date(2010,9,9) 
],
[
 "121",
"Georgia",
4436000,
0.065,
"<img src=\"http://upload.wikimedia.org/wikipedia/commons/thumb/0/0f/Flag_of_Georgia.svg/22px-Flag_of_Georgia.svg.png\">",
true,
new Date(2010,9,9) 
],
[
 "122",
"Croatia",
4435056,
0.065,
"<img src=\"http://upload.wikimedia.org/wikipedia/commons/thumb/1/1b/Flag_of_Croatia.svg/22px-Flag_of_Croatia.svg.png\">",
true,
new Date(2010,9,9) 
],
[
 "123",
"New Zealand",
4393000,
0.064,
"<img src=\"http://upload.wikimedia.org/wikipedia/commons/thumb/3/3e/Flag_of_New_Zealand.svg/22px-Flag_of_New_Zealand.svg.png\">",
true,
new Date(2010,9,9) 
],
[
 "124",
"Lebanon",
4255000,
0.062,
"<img src=\"http://upload.wikimedia.org/wikipedia/commons/thumb/5/59/Flag_of_Lebanon.svg/22px-Flag_of_Lebanon.svg.png\">",
true,
new Date(2010,9,9) 
],
[
 "125",
"Liberia",
4102000,
0.06,
"<img src=\"http://upload.wikimedia.org/wikipedia/commons/thumb/b/b8/Flag_of_Liberia.svg/22px-Flag_of_Liberia.svg.png\">",
true,
new Date(2010,9,9) 
],
[
 "127",
"Palestinian territories",
3935249,
0.055,
"<img src=\"http://upload.wikimedia.org/wikipedia/commons/thumb/0/00/Flag_of_Palestine.svg/22px-Flag_of_Palestine.svg.png\">",
true,
new Date(2010,9,9) 
],
[
 "128",
"Bosnia and Herzegovina",
3760000,
0.055,
"<img src=\"http://upload.wikimedia.org/wikipedia/commons/thumb/b/bf/Flag_of_Bosnia_and_Herzegovina.svg/22px-Flag_of_Bosnia_and_Herzegovina.svg.png\">",
true,
new Date(2010,9,9) 
],
[
 "129",
"Republic of the Congo",
3759000,
0.055,
"<img src=\"http://upload.wikimedia.org/wikipedia/commons/thumb/9/92/Flag_of_the_Republic_of_the_Congo.svg/22px-Flag_of_the_Republic_of_the_Congo.svg.png\">",
true,
new Date(2010,9,9) 
],
[
 "130",
"Moldova",
3563800,
0.052,
"<img src=\"http://upload.wikimedia.org/wikipedia/commons/thumb/2/27/Flag_of_Moldova.svg/22px-Flag_of_Moldova.svg.png\">",
true,
new Date(2010,9,9) 
],
[
 "131",
"Uruguay",
3372000,
0.049,
"<img src=\"http://upload.wikimedia.org/wikipedia/commons/thumb/f/fe/Flag_of_Uruguay.svg/22px-Flag_of_Uruguay.svg.png\">",
true,
new Date(2010,9,9) 
],
[
 "132",
"Mauritania",
3366000,
0.049,
"<img src=\"http://upload.wikimedia.org/wikipedia/commons/thumb/4/43/Flag_of_Mauritania.svg/22px-Flag_of_Mauritania.svg.png\">",
true,
new Date(2010,9,9) 
],
[
 "133",
"Lithuania",
3329227,
0.048,
"<img src=\"http://upload.wikimedia.org/wikipedia/commons/thumb/1/11/Flag_of_Lithuania.svg/22px-Flag_of_Lithuania.svg.png\">",
true,
new Date(2010,9,9) 
],
[
 "134",
"Panama",
3322576,
0.048,
"<img src=\"http://upload.wikimedia.org/wikipedia/commons/thumb/a/ab/Flag_of_Panama.svg/22px-Flag_of_Panama.svg.png\">",
true,
new Date(2010,9,9) 
],
[
 "135",
"Armenia",
3238000,
0.047,
"<img src=\"http://upload.wikimedia.org/wikipedia/commons/thumb/2/2f/Flag_of_Armenia.svg/22px-Flag_of_Armenia.svg.png\">",
true,
new Date(2010,9,9) 
],
[
 "136",
"Albania",
3195000,
0.046,
"<img src=\"http://upload.wikimedia.org/wikipedia/commons/thumb/3/36/Flag_of_Albania.svg/22px-Flag_of_Albania.svg.png\">",
true,
new Date(2010,9,9) 
],
[
 "137",
"Kuwait",
3051000,
0.044,
"<img src=\"http://upload.wikimedia.org/wikipedia/commons/thumb/a/aa/Flag_of_Kuwait.svg/22px-Flag_of_Kuwait.svg.png\">",
true,
new Date(2010,9,9) 
],
[
 "138",
"Oman",
2905000,
0.042,
"<img src=\"http://upload.wikimedia.org/wikipedia/commons/thumb/d/dd/Flag_of_Oman.svg/22px-Flag_of_Oman.svg.png\">",
true,
new Date(2010,9,9) 
],
[
 "139",
"Mongolia",
2776500,
0.04,
"<img src=\"http://upload.wikimedia.org/wikipedia/commons/thumb/4/4c/Flag_of_Mongolia.svg/22px-Flag_of_Mongolia.svg.png\">",
true,
new Date(2010,9,9) 
],
[
 "140",
"Jamaica",
2730000,
0.04,
"<img src=\"http://upload.wikimedia.org/wikipedia/commons/thumb/0/0a/Flag_of_Jamaica.svg/22px-Flag_of_Jamaica.svg.png\">",
true,
new Date(2010,9,9) 
],
[
 "141",
"Latvia",
2236300,
0.033,
"<img src=\"http://upload.wikimedia.org/wikipedia/commons/thumb/8/84/Flag_of_Latvia.svg/22px-Flag_of_Latvia.svg.png\">",
true,
new Date(2010,9,9) 
],
[
 "142",
"Namibia",
2212000,
0.032,
"<img src=\"http://upload.wikimedia.org/wikipedia/commons/thumb/0/00/Flag_of_Namibia.svg/22px-Flag_of_Namibia.svg.png\">",
true,
new Date(2010,9,9) 
],
[
 "143",
"Lesotho",
2084000,
0.03,
"<img src=\"http://upload.wikimedia.org/wikipedia/commons/thumb/4/4a/Flag_of_Lesotho.svg/22px-Flag_of_Lesotho.svg.png\">",
true,
new Date(2010,9,9) 
],
[
 "144",
"Slovenia",
2065720,
0.03,
"<img src=\"http://upload.wikimedia.org/wikipedia/commons/thumb/f/f0/Flag_of_Slovenia.svg/22px-Flag_of_Slovenia.svg.png\">",
true,
new Date(2010,9,9) 
],
[
 "145",
"Republic of Macedonia",
2048620,
0.03,
"<img src=\"http://upload.wikimedia.org/wikipedia/commons/thumb/f/f8/Flag_of_Macedonia.svg/22px-Flag_of_Macedonia.svg.png\">",
true,
new Date(2010,9,9) 
],
[
 "146",
"Botswana",
1978000,
0.029,
"<img src=\"http://upload.wikimedia.org/wikipedia/commons/thumb/f/fa/Flag_of_Botswana.svg/22px-Flag_of_Botswana.svg.png\">",
true,
new Date(2010,9,9) 
],
[
 "147",
"Gambia",
1751000,
0.025,
"<img src=\"http://upload.wikimedia.org/wikipedia/commons/thumb/7/77/Flag_of_The_Gambia.svg/22px-Flag_of_The_Gambia.svg.png\">",
true,
new Date(2010,9,9) 
],
[
 "148",
"Qatar",
1696563,
0.025,
"<img src=\"http://upload.wikimedia.org/wikipedia/commons/thumb/6/65/Flag_of_Qatar.svg/22px-Flag_of_Qatar.svg.png\">",
true,
new Date(2010,9,9) 
],
[
 "149",
"Guinea-Bissau",
1647000,
0.024,
"<img src=\"http://upload.wikimedia.org/wikipedia/commons/thumb/0/01/Flag_of_Guinea-Bissau.svg/22px-Flag_of_Guinea-Bissau.svg.png\">",
true,
new Date(2010,9,9) 
],
[
 "150",
"Gabon",
1501000,
0.022,
"<img src=\"http://upload.wikimedia.org/wikipedia/commons/thumb/0/04/Flag_of_Gabon.svg/22px-Flag_of_Gabon.svg.png\">",
true,
new Date(2010,9,9) 
],
[
 "151",
"Trinidad and Tobago",
1344000,
0.02,
"<img src=\"http://upload.wikimedia.org/wikipedia/commons/thumb/6/64/Flag_of_Trinidad_and_Tobago.svg/22px-Flag_of_Trinidad_and_Tobago.svg.png\">",
true,
new Date(2010,9,9) 
],
[
 "152",
"Estonia",
1340127,
0.019,
"<img src=\"http://upload.wikimedia.org/wikipedia/commons/thumb/8/8f/Flag_of_Estonia.svg/22px-Flag_of_Estonia.svg.png\">",
true,
new Date(2010,9,9) 
],
[
 "153",
"Mauritius",
1297000,
0.019,
"<img src=\"http://upload.wikimedia.org/wikipedia/commons/thumb/7/77/Flag_of_Mauritius.svg/22px-Flag_of_Mauritius.svg.png\">",
true,
new Date(2010,9,9) 
],
[
 "154",
"Swaziland",
1202000,
0.017,
"<img src=\"http://upload.wikimedia.org/wikipedia/commons/thumb/1/1e/Flag_of_Swaziland.svg/22px-Flag_of_Swaziland.svg.png\">",
true,
new Date(2010,9,9) 
],
[
 "155",
"East Timor",
1171000,
0.017,
"<img src=\"http://upload.wikimedia.org/wikipedia/commons/thumb/2/26/Flag_of_East_Timor.svg/22px-Flag_of_East_Timor.svg.png\">",
true,
new Date(2010,9,9) 
],
[
 "156",
"Djibouti",
879000,
0.013,
"<img src=\"http://upload.wikimedia.org/wikipedia/commons/thumb/3/34/Flag_of_Djibouti.svg/22px-Flag_of_Djibouti.svg.png\">",
true,
new Date(2010,9,9) 
],
[
 "157",
"Fiji",
854000,
0.012,
"<img src=\"http://upload.wikimedia.org/wikipedia/commons/thumb/b/ba/Flag_of_Fiji.svg/22px-Flag_of_Fiji.svg.png\">",
true,
new Date(2010,9,9) 
],
[
 "158",
"Bahrain",
807000,
0.012,
"<img src=\"http://upload.wikimedia.org/wikipedia/commons/thumb/2/2c/Flag_of_Bahrain.svg/22px-Flag_of_Bahrain.svg.png\">",
true,
new Date(2010,9,9) 
],
[
 "159",
"Cyprus",
801851,
0.012,
"<img src=\"http://upload.wikimedia.org/wikipedia/commons/thumb/d/d4/Flag_of_Cyprus.svg/22px-Flag_of_Cyprus.svg.png\">",
true,
new Date(2010,9,9) 
],
[
 "160",
"Guyana",
761000,
0.011,
"<img src=\"http://upload.wikimedia.org/wikipedia/commons/thumb/9/99/Flag_of_Guyana.svg/22px-Flag_of_Guyana.svg.png\">",
true,
new Date(2010,9,9) 
],
[
 "161",
"Bhutan",
708000,
0.01,
"<img src=\"http://upload.wikimedia.org/wikipedia/commons/thumb/9/91/Flag_of_Bhutan.svg/22px-Flag_of_Bhutan.svg.png\">",
true,
new Date(2010,9,9) 
],
[
 "162",
"Equatorial Guinea",
693000,
0.01,
"<img src=\"http://upload.wikimedia.org/wikipedia/commons/thumb/3/31/Flag_of_Equatorial_Guinea.svg/22px-Flag_of_Equatorial_Guinea.svg.png\">",
true,
new Date(2010,9,9) 
],
[
 "163",
"Comoros",
691000,
0.01,
"<img src=\"http://upload.wikimedia.org/wikipedia/commons/thumb/9/94/Flag_of_the_Comoros.svg/22px-Flag_of_the_Comoros.svg.png\">",
true,
new Date(2010,9,9) 
],
[
 "164",
"Montenegro",
626000,
0.009,
"<img src=\"http://upload.wikimedia.org/wikipedia/commons/thumb/6/64/Flag_of_Montenegro.svg/22px-Flag_of_Montenegro.svg.png\">",
true,
new Date(2010,9,9) 
],
[
 "166",
"Solomon Islands",
536000,
0.008,
"<img src=\"http://upload.wikimedia.org/wikipedia/commons/thumb/7/74/Flag_of_the_Solomon_Islands.svg/22px-Flag_of_the_Solomon_Islands.svg.png\">",
true,
new Date(2010,9,9) 
],
[
 "167",
"Western Sahara",
530000,
0.008,
"<img src=\"http://upload.wikimedia.org/wikipedia/commons/thumb/c/c8/Flag_of_Western_Sahara.svg/22px-Flag_of_Western_Sahara.svg.png\">",
true,
new Date(2010,9,9) 
],
[
 "168",
"Suriname",
524000,
0.008,
"<img src=\"http://upload.wikimedia.org/wikipedia/commons/thumb/6/60/Flag_of_Suriname.svg/22px-Flag_of_Suriname.svg.png\">",
true,
new Date(2010,9,9) 
],
[
 "169",
"Cape Verde",
513000,
0.007,
"<img src=\"http://upload.wikimedia.org/wikipedia/commons/thumb/3/38/Flag_of_Cape_Verde.svg/22px-Flag_of_Cape_Verde.svg.png\">",
true,
new Date(2010,9,9) 
],
[
 "170",
"Luxembourg",
502207,
0.007,
"<img src=\"http://upload.wikimedia.org/wikipedia/commons/thumb/d/da/Flag_of_Luxembourg.svg/22px-Flag_of_Luxembourg.svg.png\">",
true,
new Date(2010,9,9) 
],
[
 "171",
"Malta",
416333,
0.006,
"<img src=\"http://upload.wikimedia.org/wikipedia/commons/thumb/7/73/Flag_of_Malta.svg/22px-Flag_of_Malta.svg.png\">",
true,
new Date(2010,9,9) 
],
[
 "172",
"Brunei",
407000,
0.006,
"<img src=\"http://upload.wikimedia.org/wikipedia/commons/thumb/9/9c/Flag_of_Brunei.svg/22px-Flag_of_Brunei.svg.png\">",
true,
new Date(2010,9,9) 
],
[
 "173",
"Bahamas",
346000,
0.005,
"<img src=\"http://upload.wikimedia.org/wikipedia/commons/thumb/9/93/Flag_of_the_Bahamas.svg/22px-Flag_of_the_Bahamas.svg.png\">",
true,
new Date(2010,9,9) 
],
[
 "174",
"Belize",
322100,
0.005,
"<img src=\"http://upload.wikimedia.org/wikipedia/commons/thumb/e/e7/Flag_of_Belize.svg/22px-Flag_of_Belize.svg.png\">",
true,
new Date(2010,9,9) 
],
[
 "175",
"Iceland",
318006,
0.005,
"<img src=\"http://upload.wikimedia.org/wikipedia/commons/thumb/c/ce/Flag_of_Iceland.svg/22px-Flag_of_Iceland.svg.png\">",
true,
new Date(2010,9,9) 
],
[
 "176",
"Maldives",
314000,
0.005,
"<img src=\"http://upload.wikimedia.org/wikipedia/commons/thumb/0/0f/Flag_of_Maldives.svg/22px-Flag_of_Maldives.svg.png\">",
true,
new Date(2010,9,9) 
],
[
 "177",
"Barbados",
257000,
0.004,
"<img src=\"http://upload.wikimedia.org/wikipedia/commons/thumb/e/ef/Flag_of_Barbados.svg/22px-Flag_of_Barbados.svg.png\">",
true,
new Date(2010,9,9) 
],
[
 "178",
"Vanuatu",
246000,
0.004,
"<img src=\"http://upload.wikimedia.org/wikipedia/commons/thumb/b/bc/Flag_of_Vanuatu.svg/22px-Flag_of_Vanuatu.svg.png\">",
true,
new Date(2010,9,9) 
],
[
 "181",
"Samoa",
179000,
0.003,
"<img src=\"http://upload.wikimedia.org/wikipedia/commons/thumb/3/31/Flag_of_Samoa.svg/22px-Flag_of_Samoa.svg.png\">",
true,
new Date(2010,9,9) 
],
[
 "182",
"Saint Lucia",
174000,
0.003,
"<img src=\"http://upload.wikimedia.org/wikipedia/commons/thumb/9/9f/Flag_of_Saint_Lucia.svg/22px-Flag_of_Saint_Lucia.svg.png\">",
true,
new Date(2010,9,9) 
],
[
 "183",
"Sao Tome and Principe",
165000,
0.002,
"<img src=\"http://upload.wikimedia.org/wikipedia/commons/thumb/4/4f/Flag_of_Sao_Tome_and_Principe.svg/22px-Flag_of_Sao_Tome_and_Principe.svg.png\">",
true,
new Date(2010,9,9) 
],
[
 "184",
"Federated States of Micronesia",
111000,
0.002,
"<img src=\"http://upload.wikimedia.org/wikipedia/commons/thumb/4/4c/Flag_of_Federated_States_of_Micronesia.svg/22px-Flag_of_Federated_States_of_Micronesia.svg.png\">",
true,
new Date(2010,9,9) 
],
[
 "186",
"Saint Vincent and the Grenadines",
109000,
0.002,
"<img src=\"http://upload.wikimedia.org/wikipedia/commons/thumb/6/6d/Flag_of_Saint_Vincent_and_the_Grenadines.svg/22px-Flag_of_Saint_Vincent_and_the_Grenadines.svg.png\">",
true,
new Date(2010,9,9) 
],
[
 "188",
"Grenada",
104000,
0.002,
"<img src=\"http://upload.wikimedia.org/wikipedia/commons/thumb/b/bc/Flag_of_Grenada.svg/22px-Flag_of_Grenada.svg.png\">",
true,
new Date(2010,9,9) 
],
[
 "189",
"Tonga",
104000,
0.002,
"<img src=\"http://upload.wikimedia.org/wikipedia/commons/thumb/9/9a/Flag_of_Tonga.svg/22px-Flag_of_Tonga.svg.png\">",
true,
new Date(2010,9,9) 
],
[
 "190",
"Kiribati",
100000,
0.001,
"<img src=\"http://upload.wikimedia.org/wikipedia/commons/thumb/d/d3/Flag_of_Kiribati.svg/22px-Flag_of_Kiribati.svg.png\">",
true,
new Date(2010,9,9) 
],
[
 "192",
"Antigua and Barbuda",
89000,
0.001,
"<img src=\"http://upload.wikimedia.org/wikipedia/commons/thumb/8/89/Flag_of_Antigua_and_Barbuda.svg/22px-Flag_of_Antigua_and_Barbuda.svg.png\">",
true,
new Date(2010,9,9) 
],
[
 "194",
"Seychelles",
85000,
0.001,
"<img src=\"http://upload.wikimedia.org/wikipedia/commons/thumb/9/92/Flag_of_the_Seychelles.svg/22px-Flag_of_the_Seychelles.svg.png\">",
true,
new Date(2010,9,9) 
],
[
 "195",
"Andorra",
84082,
0.001,
"<img src=\"http://upload.wikimedia.org/wikipedia/commons/thumb/1/19/Flag_of_Andorra.svg/22px-Flag_of_Andorra.svg.png\">",
true,
new Date(2010,9,9) 
],
[
 "198",
"Dominica",
67000,
0.001,
"<img src=\"http://upload.wikimedia.org/wikipedia/commons/thumb/c/c4/Flag_of_Dominica.svg/22px-Flag_of_Dominica.svg.png\">",
true,
new Date(2010,9,9) 
],
[
 "200",
"Marshall Islands",
63000,
0.001,
"<img src=\"http://upload.wikimedia.org/wikipedia/commons/thumb/2/2e/Flag_of_the_Marshall_Islands.svg/22px-Flag_of_the_Marshall_Islands.svg.png\">",
true,
new Date(2010,9,9) 
],
[
 "204",
"Saint Kitts and Nevis",
52000,
0.001,
"<img src=\"http://upload.wikimedia.org/wikipedia/commons/thumb/f/fe/Flag_of_Saint_Kitts_and_Nevis.svg/22px-Flag_of_Saint_Kitts_and_Nevis.svg.png\">",
true,
new Date(2010,9,9) 
],
[
 "206",
"Liechtenstein",
35904,
5e-04,
"<img src=\"http://upload.wikimedia.org/wikipedia/commons/thumb/4/47/Flag_of_Liechtenstein.svg/22px-Flag_of_Liechtenstein.svg.png\">",
true,
new Date(2010,9,9) 
],
[
 "207",
"Monaco",
33000,
5e-04,
"<img src=\"http://upload.wikimedia.org/wikipedia/commons/thumb/e/ea/Flag_of_Monaco.svg/22px-Flag_of_Monaco.svg.png\">",
true,
new Date(2010,9,9) 
],
[
 "209",
"San Marino",
31794,
5e-04,
"<img src=\"http://upload.wikimedia.org/wikipedia/commons/thumb/b/b1/Flag_of_San_Marino.svg/22px-Flag_of_San_Marino.svg.png\">",
true,
new Date(2010,9,9) 
],
[
 "213",
"Palau",
20000,
3e-04,
"<img src=\"http://upload.wikimedia.org/wikipedia/commons/thumb/4/48/Flag_of_Palau.svg/22px-Flag_of_Palau.svg.png\">",
true,
new Date(2010,9,9) 
],
[
 "215",
"Tuvalu",
10000,
1e-04,
"<img src=\"http://upload.wikimedia.org/wikipedia/commons/thumb/3/38/Flag_of_Tuvalu.svg/22px-Flag_of_Tuvalu.svg.png\">",
true,
new Date(2010,9,9) 
],
[
 "216",
"Nauru",
10000,
1e-04,
"<img src=\"http://upload.wikimedia.org/wikipedia/commons/thumb/3/30/Flag_of_Nauru.svg/22px-Flag_of_Nauru.svg.png\">",
true,
new Date(2010,9,9) 
],
[
 "222",
"Vatican City",
800,
2e-05,
"<img src=\"http://upload.wikimedia.org/wikipedia/commons/thumb/0/00/Flag_of_the_Vatican_City.svg/20px-Flag_of_the_Vatican_City.svg.png\">",
true,
new Date(2010,9,9) 
] 
];
data.addColumn('string','Rank');
data.addColumn('string','Country');
data.addColumn('number','Population');
data.addColumn('number','% of World Population');
data.addColumn('string','Flag');
data.addColumn('boolean','Mode');
data.addColumn('date','Date');
data.addRows(datajson);
return(data);
}
 
// jsDrawChart
function drawChartTableIDd2c5e47b65() {
var data = gvisDataTableIDd2c5e47b65();
var options = {};
options["allowHtml"] = true;
options["page"] = "enable";

  var dataFormat1 = new google.visualization.NumberFormat({pattern:"#,###"});
  dataFormat1.format(data, 2);
  var dataFormat2 = new google.visualization.NumberFormat({pattern:"#.#%"});
  dataFormat2.format(data, 3);

    var chart = new google.visualization.Table(
    document.getElementById('TableIDd2c5e47b65')
    );
    chart.draw(data,options);
    

}
  
 
// jsDisplayChart
(function() {
var pkgs = window.__gvisPackages = window.__gvisPackages || [];
var callbacks = window.__gvisCallbacks = window.__gvisCallbacks || [];
var chartid = "table";
  
// Manually see if chartid is in pkgs (not all browsers support Array.indexOf)
var i, newPackage = true;
for (i = 0; newPackage && i < pkgs.length; i++) {
if (pkgs[i] === chartid)
newPackage = false;
}
if (newPackage)
  pkgs.push(chartid);
  
// Add the drawChart function to the global list of callbacks
callbacks.push(drawChartTableIDd2c5e47b65);
})();
function displayChartTableIDd2c5e47b65() {
  var pkgs = window.__gvisPackages = window.__gvisPackages || [];
  var callbacks = window.__gvisCallbacks = window.__gvisCallbacks || [];
  window.clearTimeout(window.__gvisLoad);
  // The timeout is set to 100 because otherwise the container div we are
  // targeting might not be part of the document yet
  window.__gvisLoad = setTimeout(function() {
  var pkgCount = pkgs.length;
  google.load("visualization", "1", { packages:pkgs, callback: function() {
  if (pkgCount != pkgs.length) {
  // Race condition where another setTimeout call snuck in after us; if
  // that call added a package, we must not shift its callback
  return;
}
while (callbacks.length > 0)
callbacks.shift()();
} });
}, 100);
}
 
// jsFooter
</script>
 
<!-- jsChart -->  
<script type="text/javascript" src="https://www.google.com/jsapi?callback=displayChartTableIDd2c5e47b65"></script>
 
<!-- divChart -->
  
<div id="TableIDd2c5e47b65" 
  style="width: 500; height: automatic;">
</div>

---
## Organization Chart (double-click)


```r
Org <- gvisOrgChart(Regions, 
                    options=list(width=600, height=250,
                                 size='large', allowCollapse=TRUE))
plot(Org)
```

<!-- OrgChart generated in R 3.1.1 by googleVis 0.5.5 package -->
<!-- Tue Oct 14 16:33:14 2014 -->


<!-- jsHeader -->
<script type="text/javascript">
 
// jsData 
function gvisDataOrgChartIDd2c117b7716 () {
var data = new google.visualization.DataTable();
var datajson =
[
 [
 "Global",
null,
"10" 
],
[
 "America",
"Global",
"2" 
],
[
 "Europe",
"Global",
"99" 
],
[
 "Asia",
"Global",
"10" 
],
[
 "France",
"Europe",
"71" 
],
[
 "Sweden",
"Europe",
"89" 
],
[
 "Germany",
"Europe",
"58" 
],
[
 "Mexico",
"America",
"2" 
],
[
 "USA",
"America",
"38" 
],
[
 "China",
"Asia",
"5" 
],
[
 "Japan",
"Asia",
"48" 
] 
];
data.addColumn('string','Region');
data.addColumn('string','Parent');
data.addColumn('string','Val');
data.addRows(datajson);
return(data);
}
 
// jsDrawChart
function drawChartOrgChartIDd2c117b7716() {
var data = gvisDataOrgChartIDd2c117b7716();
var options = {};
options["width"] =    600;
options["height"] =    250;
options["size"] = "large";
options["allowCollapse"] = true;

    var chart = new google.visualization.OrgChart(
    document.getElementById('OrgChartIDd2c117b7716')
    );
    chart.draw(data,options);
    

}
  
 
// jsDisplayChart
(function() {
var pkgs = window.__gvisPackages = window.__gvisPackages || [];
var callbacks = window.__gvisCallbacks = window.__gvisCallbacks || [];
var chartid = "orgchart";
  
// Manually see if chartid is in pkgs (not all browsers support Array.indexOf)
var i, newPackage = true;
for (i = 0; newPackage && i < pkgs.length; i++) {
if (pkgs[i] === chartid)
newPackage = false;
}
if (newPackage)
  pkgs.push(chartid);
  
// Add the drawChart function to the global list of callbacks
callbacks.push(drawChartOrgChartIDd2c117b7716);
})();
function displayChartOrgChartIDd2c117b7716() {
  var pkgs = window.__gvisPackages = window.__gvisPackages || [];
  var callbacks = window.__gvisCallbacks = window.__gvisCallbacks || [];
  window.clearTimeout(window.__gvisLoad);
  // The timeout is set to 100 because otherwise the container div we are
  // targeting might not be part of the document yet
  window.__gvisLoad = setTimeout(function() {
  var pkgCount = pkgs.length;
  google.load("visualization", "1", { packages:pkgs, callback: function() {
  if (pkgCount != pkgs.length) {
  // Race condition where another setTimeout call snuck in after us; if
  // that call added a package, we must not shift its callback
  return;
}
while (callbacks.length > 0)
callbacks.shift()();
} });
}, 100);
}
 
// jsFooter
</script>
 
<!-- jsChart -->  
<script type="text/javascript" src="https://www.google.com/jsapi?callback=displayChartOrgChartIDd2c117b7716"></script>
 
<!-- divChart -->
  
<div id="OrgChartIDd2c117b7716" 
  style="width: 600; height: 250;">
</div>

---
## Tree Map (left/right clicks)


```r
Tree <- gvisTreeMap(Regions,  
                    "Region", "Parent", 
                    "Val", "Fac", 
                    options=list(fontSize=16))
plot(Tree)
```

<!-- TreeMap generated in R 3.1.1 by googleVis 0.5.5 package -->
<!-- Tue Oct 14 16:33:14 2014 -->


<!-- jsHeader -->
<script type="text/javascript">
 
// jsData 
function gvisDataTreeMapIDd2c34af844 () {
var data = new google.visualization.DataTable();
var datajson =
[
 [
 "Global",
null,
10,
2 
],
[
 "America",
"Global",
2,
4 
],
[
 "Europe",
"Global",
99,
11 
],
[
 "Asia",
"Global",
10,
8 
],
[
 "France",
"Europe",
71,
2 
],
[
 "Sweden",
"Europe",
89,
3 
],
[
 "Germany",
"Europe",
58,
10 
],
[
 "Mexico",
"America",
2,
9 
],
[
 "USA",
"America",
38,
11 
],
[
 "China",
"Asia",
5,
1 
],
[
 "Japan",
"Asia",
48,
11 
] 
];
data.addColumn('string','Region');
data.addColumn('string','Parent');
data.addColumn('number','Val');
data.addColumn('number','Fac');
data.addRows(datajson);
return(data);
}
 
// jsDrawChart
function drawChartTreeMapIDd2c34af844() {
var data = gvisDataTreeMapIDd2c34af844();
var options = {};
options["width"] =    600;
options["height"] =    500;
options["fontSize"] =     16;

    var chart = new google.visualization.TreeMap(
    document.getElementById('TreeMapIDd2c34af844')
    );
    chart.draw(data,options);
    

}
  
 
// jsDisplayChart
(function() {
var pkgs = window.__gvisPackages = window.__gvisPackages || [];
var callbacks = window.__gvisCallbacks = window.__gvisCallbacks || [];
var chartid = "treemap";
  
// Manually see if chartid is in pkgs (not all browsers support Array.indexOf)
var i, newPackage = true;
for (i = 0; newPackage && i < pkgs.length; i++) {
if (pkgs[i] === chartid)
newPackage = false;
}
if (newPackage)
  pkgs.push(chartid);
  
// Add the drawChart function to the global list of callbacks
callbacks.push(drawChartTreeMapIDd2c34af844);
})();
function displayChartTreeMapIDd2c34af844() {
  var pkgs = window.__gvisPackages = window.__gvisPackages || [];
  var callbacks = window.__gvisCallbacks = window.__gvisCallbacks || [];
  window.clearTimeout(window.__gvisLoad);
  // The timeout is set to 100 because otherwise the container div we are
  // targeting might not be part of the document yet
  window.__gvisLoad = setTimeout(function() {
  var pkgCount = pkgs.length;
  google.load("visualization", "1", { packages:pkgs, callback: function() {
  if (pkgCount != pkgs.length) {
  // Race condition where another setTimeout call snuck in after us; if
  // that call added a package, we must not shift its callback
  return;
}
while (callbacks.length > 0)
callbacks.shift()();
} });
}, 100);
}
 
// jsFooter
</script>
 
<!-- jsChart -->  
<script type="text/javascript" src="https://www.google.com/jsapi?callback=displayChartTreeMapIDd2c34af844"></script>
 
<!-- divChart -->
  
<div id="TreeMapIDd2c34af844" 
  style="width: 600; height: 500;">
</div>

---
## Sankey chart


```r
datSK <- data.frame(From=c(rep("A",3), rep("B", 3)),
                    To=c(rep(c("X", "Y", "Z"),2)),
                    Weight=c(5,7,6,2,9,4))

Sankey <- gvisSankey(datSK, from="From", to="To", weight="Weight",
                     options=list(
                       sankey="{link: {color: { fill: '#d799ae' } },
                            node: { color: { fill: '#a61d4c' },
                            label: { color: '#871b47' } }}"))
print(Sankey,file="Sankey.html")
```

---

## Sankey

<iframe src="Sankey.html" width="600" height="600"></iframe>

---
## Calendar chart


```r
Cal <- gvisCalendar(Cairo, 
                    datevar="Date", 
                    numvar="Temp",
                    options=list(
                      title="Daily temperature in Cairo",
                      height=320,
                      calendar="{yearLabel: { fontName: 'Times-Roman',
                               fontSize: 32, color: '#1A8763', bold: true},
                               cellSize: 10,
                               cellColor: { stroke: 'red', strokeOpacity: 0.2 },
                               focusedCellColor: {stroke:'red'}}")
)
print(Cal,file="Cal.html")
```

---
## Calendar chart

<iframe src="Cal.html" width="600" height="600"></iframe>


---
## Timeline chart


```r
datTL <- data.frame(Position=c(rep("President", 3), rep("Vice", 3)),
                    Name=c("Washington", "Adams", "Jefferson",
                           "Adams", "Jefferson", "Burr"),
                    start=as.Date(x=rep(c("1789-03-29", "1797-02-03", 
                                          "1801-02-03"),2)),
                    end=as.Date(x=rep(c("1797-02-03", "1801-02-03", 
                                        "1809-02-03"),2)))

Timeline <- gvisTimeline(data=datTL, 
                         rowlabel="Name",
                         barlabel="Position",
                         start="start", 
                         end="end",
                         options=list(timeline="{groupByRowLabel:false}",
                                      backgroundColor='#ffd', 
                                      height=350,
                                      colors="['#cbb69d', '#603913', '#c69c6e']"))
print(Timeline,file="Timeline.html")
```

---
## Timeline chart

<iframe src="Timeline.html" width="600" height="600"></iframe>


---
## Intensity Map


```r
Intensity <- gvisIntensityMap(df,options=list( width=750, height=400))
print(Intensity,file="Intensity.html")
```
<iframe src="Intensity.html" width="600" height="600"></iframe>

---
## Geo Chart


```r
Geo=gvisGeoChart(Exports, locationvar="Country", 
                 colorvar="Profit",
                 options=list(projection="kavrayskiy-vii",
                 width=750, height=400))
print(Geo,file="Geo.html")
```
<iframe src="Geo.html" width="600" height="600"></iframe>

---
## Geo chart US


```r
library(datasets)
states <- data.frame(state.name, state.x77)
GeoStates <- gvisGeoChart(states, "state.name", "Illiteracy",
                          options=list(region="US", displayMode="regions", resolution="provinces",
                                       width=600, height=400))
print(GeoStates,file="GeoStates.html")
```
<iframe src="GeoStates.html" width="600" height="600"></iframe>

---
## Geo markers: Hurricane Andrew track


```r
GeoMarker <- gvisGeoChart(Andrew, "LatLong", 
                          sizevar='Speed_kt',
                          colorvar="Pressure_mb", 
                          options=list(region="US"))
print(GeoMarker,file="GeoMarker.html")
```
<iframe src="GeoMarker.html" width="600" height="600"></iframe>

---
## Google map: Hurricane Andrew Track


```r
AndrewMap <- gvisMap(Andrew, "LatLong" , "Tip", 
                     options=list(showTip=TRUE, 
                                  showLine=TRUE, 
                                  enableScrollWheel=TRUE,
                                  mapType='terrain', 
                                  useMapTypeControl=TRUE))
print(AndrewMap,file="AndrewMap.html")
```
<iframe src="AndrewMap.html" width="600" height="600"></iframe>

---
## Geo Map: Hurricane Andrew Track


```r
AndrewGeo <- gvisGeoMap(Andrew, 
                        locationvar="LatLong", 
                        numvar="Speed_kt", 
                        hovervar="Category", 
                        options=list(height=350, 
                                     region="US", 
                                     dataMode="markers"))
print(AndrewGeo,file="AndrewGeo.html")
```
<iframe src="AndrewGeo.html" width="600" height="600"></iframe>

---
## Merging


```r
G <- gvisGeoChart(Exports, "Country", "Profit", 
                  options=list(width=600, height=400))
T <- gvisTable(Exports, 
               options=list(width=440, height=400))

GT <- gvisMerge(G,T, horizontal=TRUE) 
print(GT,file="GT.html")
```
<iframe src="GT.html" width="600" height="600"></iframe>

---

## Your turn to have fun!!

Code for this deck can be found at: https://github.com/patilv/googleVis-tutorial

