<!DOCTYPE html>
<html>
  <head>
    <title>Title</title>
    <meta charset="utf-8">
    <style>
      @import url(https://fonts.googleapis.com/css?family=Yanone+Kaffeesatz);
      @import url(https://fonts.googleapis.com/css?family=Droid+Serif:400,700,400italic);
      @import url(https://fonts.googleapis.com/css?family=Ubuntu+Mono:400,700,400italic);

      body { font-family: 'Droid Serif'; }
      h1, h2, h3 {
        font-family: 'Yanone Kaffeesatz';
        font-weight: normal;
      }
      .remark-code, .remark-inline-code { font-family: 'Ubuntu Mono'; }
      body {
        font-family: 'Droid Serif';
      }
      h1, h2, h3 {
        font-family: 'Yanone Kaffeesatz';
        font-weight: 400;
        margin-bottom: 0;
      }
      .remark-slide-content h1 { font-size: 3em; }
      .remark-slide-content h2 { font-size: 2em; }
      .remark-slide-content h3 { font-size: 1.6em; }
      .footnote {
        position: absolute;
        bottom: 3em;
      }
      li p { line-height: 1.25em; }
      .red { color: #fa0000; }
      .large { font-size: 2em; }
      a, a > code {
        color: rgb(249, 38, 114);
        text-decoration: none;
      }
      code {
        background: #e7e8e2;
        border-radius: 5px;
      }
      .remark-code, .remark-inline-code { font-family: 'Ubuntu Mono'; }
      .remark-code-line-highlighted     { background-color: #373832; }
      .pull-left {
        float: left;
        width: 47%;
      }
      .pull-right {
        float: right;
        width: 47%;
      }
      .pull-right ~ p {
        clear: both;
      }
      #slideshow .slide .content code {
        font-size: 0.8em;
      }
      #slideshow .slide .content pre code {
        font-size: 0.9em;
        padding: 15px;
      }
      .inverse {
        background: #272822;
        color: #777872;
        text-shadow: 0 0 20px #333;
      }
      .inverse h1, .inverse h2 {
        color: #f3f3f3;
        line-height: 0.8em;
      }

      /* Slide-specific styling */
      #slide-inverse .footnote {
        bottom: 12px;
        left: 20px;
      }
      #slide-how .slides {
        font-size: 0.9em;
        position: absolute;
        top:  151px;
        right: 140px;
      }
      #slide-how .slides h3 {
        margin-top: 0.2em;
      }
      #slide-how .slides .first, #slide-how .slides .second {
        padding: 1px 20px;
        height: 90px;
        width: 120px;
        -moz-box-shadow: 0 0 10px #777;
        -webkit-box-shadow: 0 0 10px #777;
        box-shadow: 0 0 10px #777;
      }
      #slide-how .slides .first {
        background: #fff;
        position: absolute;
        top: 20%;
        left: 20%;
        z-index: 1;
      }
      #slide-how .slides .second {
        position: relative;
        background: #fff;
        z-index: 0;
      }

      /* Two-column layout */
      .left-column {
        color: #777;
        width: 20%;
        height: 92%;
        float: left;
      }
        .left-column h2:last-of-type, .left-column h3:last-child {
          color: #000;
        }
      .right-column {
        width: 75%;
        float: right;
        padding-top: 1em;
      }
      .right {
        float: right;
        margin-left: 1em;
      }
      .pushdown {
        margin-top: 12em;
      }
        
        .right.pushdown[![Prototypal Inheritance 2](prototype2.png)]

    </style>
  </head>
  <body>
    <textarea id="source">

name: inverse
layout: true
class: center, middle, inverse
---
#tech ~ pm
## getting under the hood
        @pshah
[ri-mahrk]
.footnote[Go directly to [project site](https://github.com/gnab/remark)]
---
## What is it and why should I be using it?
---
layout: false
.left-column[
  ## What is it?
]
.right-column[
  A simple, in-browser, Markdown-driven slideshow tool targeted at people who know their way around HTML and CSS, featuring:

- Markdown formatting, with smart extensions

- Presenter mode, with cloned slideshow view

- Syntax highlighting, supporting a range of languages

- Slide scaling, thus similar appearance on all devices / resolutions .red[*]

- Touch support for smart phones and pads, i.e. swipe to navigate slides

.footnote[.red[*] At least browsers try their best]
]
---


# Agenda

1. Under the Hood
2. Product Development Process
3. LAMP Stack vs. MEAN Stack
4. It's all Mobile
5. Models-Views-

???
<pre>      
Our hypothetical product
Looking at the stack - web tier
Looking at the stack - application tier
Looking at the stack - persistence tier
Looking at the stack - other services
Development tools - source code repository
Development tools - integrated development environment
Development tools - unit tests
Development tools - mocked services
Development tools - continuous integration server
Feature development - task estimation and selection
Feature development - breaking down the problem
Feature development - writing unit tests
Feature development - writing the code
Feature development - feedback loops
Feature development - peer code review
Feature development - QA and UAT
</pre>  
        

---
# Under the Hood

--
        
* The underlying implementation of a product (hardware, software, or idea). Implies that the implementation is not intuitively obvious from the appearance, but the speaker is about to enable the listener to grok it. "Let's now look under the hood to see how ...."
        
--
        

* Can also imply that the implementation is much simpler than the appearance would indicate: "Under the hood, we are just fork/execing the shell


---
layout: false
.left-column[
  ## Product Development Process
  ### Conceptual Product Development
]
.right-column[

- Identify Customer Needs             
- Generate Product Concepts             
- Perform Business Justification        
- Selection of Product Concept
 
.footnote[.red[*] At least browsers try their best]
]
---
# Product Development Process
        
| Conceptual Product Development        |  Technical Product Development
---|---
|---|---|
| Identify Customer Needs               |  Detailed Development Plan|
| Generate Product Concepts             |  Sprint Planning |
| Perform Business Justification        |  Unit/QA/Regression Testing  
| Selection of Product Concept          |  Release Management     | 
                


.footnote[.red.bold[*] Important footnote]        
---
---
template: inverse

## How does it work, then?
---
name: how

.left-column[
  ## How does it work?
### - Markdown
]
.right-column[
A Markdown-formatted chunk of text is transformed into individual slides by JavaScript running in the browser:

```remark
# Slide 1
This is slide 1

---

# Slide 2
This is slide 2
```

.slides[
  .first[
  ### Slide 1
  This is slide 1
  ]
  .second[
  ### Slide 2
  This is slide 2
  ]
]

Regular Markdown rules apply with only a single exception:

  - A line containing three dashes constitutes a new slide
  (not a horizontal rule, `&lt;hr /&gt;`)

Have a look at the [Markdown website](http://daringfireball.net/projects/markdown/) if you're not familiar with Markdown formatting.
]
---     
---
# LAMP Stack vs. MEAN Stack

          .right.pushdown[![Prototypal Inheritance 2](prototype2.png)]

---

# It's all Mobile these days
        <img style="width:50%"  src="newmobilestack.jpg">
          .right.pushdown[![Prototypal Inheritance 2](newmobilestack.jpg)]

---
# Code Writing and Testing

.pull-left[

<pre><code>```javascript
function add(a, b)
  return a + b
end
```</code></pre>
]
.pull-right[

<pre><code>```ruby
def add(a, b)
  a + b
end
```</code></pre>
]

---
# Full Stack Layers

Server, Network, and Hosting Environment
Data Modelling
Business / Domain Logic
API layer / MVC 
User Interface
User Experience
 
Front-end 
Back-end
Database
    
---
Here's our logo (hover to see the title text):

Inline-style: 
![alt text](https://github.com/adam-p/markdown-here/raw/master/src/common/images/icon48.png "Logo Title Text 1")

Reference-style: 
![alt text][logo]

[logo]: https://github.com/adam-p/markdown-here/raw/master/src/common/images/icon48.png "Logo Title Text 2"

---
# That's all folks!

Slideshow created with [remark](http://gnab.github.com/remark).
        
        
    </textarea>
    <script src="https://gnab.github.io/remark/downloads/remark-latest.min.js">
    </script>
    <script>
      var slideshow = remark.create();
    </script>
  </body>
</html>