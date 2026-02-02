# 02-DataVis-5ways

# Vega-Lite
I already have some familiarity with Vega-Lite because of my work with it in my MQP, so the process of creating the visualization went pretty smoothly. Although I hadn't worked with scatterplots in Vega-Lite before, the documentation for the grammar is thorough yet easy to understand, so I was able to find the properties I needed to add to recreate the graph without too much trouble. After adding the reference to the CSV file in my Vega-Lite code, all I needed to change was the properties inside the "mark" property to get the visualization looking the same. The main problem I had was that when I changed the bill length legend to look like the example, the labels for "40" and "50" overlapped the symbols. I wasn't able to find a fix for this, since properties that sounded like they would fix it like "labelPadding" didn't seem to have any effect, so I instead removed the legend entirely.

!["Vega-Lite visualization"](img/vega-lite.png)

I can definitely see Vega-Lite being used to create visualizations in many fields, as long as they don't need too much customization, since the ease of use makes up for its limits.

I started with the basic HTML file used on the "Embedding Vega-Lite" page on Vega's website.


# d3
Recreating the graph in D3 took some more getting used to than it did with Vega-Lite. I had to do some digging in the documentation to find what I was looking for (though I do appreciate the index tab that lets you ctrl + F to find specific sections), and the fact that most examples of functions were isolated and don't show their locations in code means that implementation of them can be a game of trial and error. Sometimes I'd find a few simple D3 examples online to see the functions I wanted to use in action, so I could use them myself. Defining scales that are then set to parts of the svg took longer to figure out than I think it should've because of how the documentation is set up, but once I got the hang of it they made recreating properties of the scatterplot fairly smooth. One difficulty was adding labels to the graphs, in which D3 doesn't have as simple as Vega-Lite's "title" property for axes. Instead, I had to create text objects and set their positions manually. One other difficulty I had was getting the ticks to look the same as the example. There is a ticks function with a start, stop, and count, but giving it a discrete start and stop messed up the count for me for some reason. If I gave it just a count variable it would work, but I'd need to provide the count necessary to get the x-axis to increment by 10, instead of being able to specify directly that I want it to increment by 10.

!["d3 visualization"](img/d3.png)

D3 is definitely useful for people familiar with programming, but it doesn't have the same intuitiveness that Vega-Lite does, which makes it have a steeper learning curve that may drive non-programmers away. But a benefit to D3 is that while implementing some features in the visualization was more difficult than in Vega-Lite, the way it's set up allows for a lot more customization. I can see D3 being useful for when a more specialized visualization is required and the team has someone with a web development background that won't take as long to get comfortable with D3.

I started with the code in the "D3 in Vanilla HTML" section of the "Getting started" tab on D3's documentation.

# Altair

Altair was just as intuitive as Vega-Lite was and the process of replicating the visualization went very smoothly. Using its syntax you can create the graph with concise code. With Altair, I could encode the X axis, Y axis, color, and size to their respective fields, and then add properties to them to customize them how I wanted. The legends for size and color were generated without any code, but could also be customized if need be. The only obstacle I faced was some issues with pip install when installing Altair, compared to Vega-Lite where I faced no problems when embedding it in an HTML site.

!["Altair visualization"](img/altair.png)

I can see Altair being useful in a similar way with Vega-Lite, where it's accessibility lowers the entry barrier for people looking to create a visualization. I believe that Vega-Lite would still be more appealing to non-programmers with their online editor and JSON syntax, but any team looking to create a quick but effective visualization wouldn't go wrong choosing Altair.

# Flourish
Flourish is the only tool I chose that doesn't require any coding or creating JSON objects, and is instead heavily GUI focused. While that does limit your options somewhat, there were enough to let me recreate the graph fairly accurately. I like the data tab, which lets you easily select which fields correlate to the X axis, Y axis, colors, size, etc. This plus the amount of options offers some decent customization. Though one drawback to the size variation is that despite setting the bill length field to the size of each point and the size variation from 10 to 350, the size difference between points is barely noticeable. This seems to be because it's scaling with the smallest size being 0 rather than the minimum bill length, so when referenced to 0, a bill length of 40 and 50 will look almost the same. Also, while I was able to create this graph for free, Flourish does have some paid features.

!["Flourish visualization"](img/flourish.png)

Although Vega-Lite and Altair are both intuitive in their syntax, I can still see them being intimidating to someone with no coding experience, and that they'd much prefer a tool with a GUI like Flourish. Although Flourish doesn't have the flexibility that other tools and libraries have, it has enough features that it would work well for a team in which no members have any experience programming.

# R + ggplot2
Out of all 5 visualization methods, I found this one to be the least intuitive. Though d3 is more complex, the syntax of it is easier to read at a glance and find out what they're doing. It might be partly because I'm not familiar with R, but I found it hard to navigate the documentation of ggplot with everything being short abbreviations, or even single letters, and it made creating the graph tougher as a newcomer to R. The benefits were that I didn't need to make any changes to get the ticks at reasonable intervals or have scales not start at 0. While it does have good customization like Vega-Lite and Altair, the syntax structure would take some getting used to if I were to make a more complex visualization than this one with ggplot2.

!["ggplot2 visualization"](img/ggplot2.png)

This would likely be best for someone that's already familiar with R and could easily transfer their skills into creating visualizations. In that case, it will likely be easier to get a visualization started with ggplot2, as you can create a solid visualization with very little and tweak it from there. I don't feel like it would be a good recommendation to learn for complex visualizations, because ggplot2 would take some getting used to, and if you're going to learn a library, learning the more versatile d3 would likely be the preferable choice.

Assignment 2 - Data Visualization, 5 Ways  
===

Now that you have successfully made a "visualization" of shapes and lines using d3, your next assignment is to successfully make a *actual visualization*... 5 times. 

The goal of this project is to gain experience with as many data visualization libraries, languages, and tools as possible.

I have provided a small dataset about penguins, `penglings.csv`.
Each row contains a penguin observation and several variables about it, including bill length, flipper length, and more.

Your goal is to use 5 different tools to make the following chart:

These features should be preserved as much as possible in your replication:

- Data positioning: it should be a upward-trending scatterplot as shown.  Flipper Length should be on the x-axis and Body Mass on the y-axis.
- Scales: Note the scales do not start at 0.
- Axis ticks and labels: both axes are labeled and there are tick marks at a reasonable interval, e.g 10, 20, 30, etc.
- Color mapping to species.
- Size mapping to Bill Length.
- Opacity of circles set to 0.8 or similar for a semi-transparent effect.

Other features are not required. This includes:

- The background grid.
- The legends.

Note that some software packages will make it **impossible** to perfectly preserve the above requirements. 
Be sure to note where these deviate as you reflect on what a tool is good for.

Improvements are also welcome as part of Technical and Design achievements.

Libraries, Tools, Languages
---

You are required to use 5 different tools or libraries.
Of the 5 tools, you must use at least 3 libraries (libraries require code of some kind).
This could be `Python, R, Javascript`, or `Java, Javascript, Matlab` or any other combination.
Dedicated tools (i.e. Excel) do not count towards the language requirement.

Otherwise, you should seek tools and libraries to fill out your 5.

Below are a few ideas. Do not limit yourself to this list!
There are new tools coming out every year and we may not have an exhaustive list of the latest and greatest.

Some may be difficult choices, like Matlab or SPSS, which require large installations, licenses, and occasionally difficult UIs.

I have marked a few that are strongly suggested.

- *R + ggplot2* `<- definitely worth trying`
- Excel
- *d3* `<- since the rest of the class uses this, we're requiring it`
- *Altair* `<- hugely popular python library. highly recommended `
- three.js `<- well, it's a 3d library. not really recommended, but could be interesting and fun`
- p5js `<- good for playing around. not really a chart lib`
- Tableau
- PowerBI
- *Vega-lite* <- `<- very interesting formal visualization model; might be the future of the field`
- Flourish <- `<- popular in recent years`
- *DataWrapper* <- `<- popular in recent years`
- GNUplot `<- the former CS department head uses this all the time :)`
- SAS/SPSS/Matlab

You may write everything from scratch, or start with demo programs from books or the web. 
If you do start with code that you found, please identify the source of the code in your README and, most importantly, make non-trivial changes to the code to make it your own so you really learn what you're doing. 

Tips
---

- If you're using d3, key to this assignment is knowing how to load data.
You will likely use the [`d3.json` or `d3.csv` functions](https://d3js.org/d3-dsv) to load the data you found.

**Beware that these functions are *asynchronous*, meaning it's possible to "build" an empty visualization before the data actually loads. Figuring out how to do this properly can be a major hiccup if you haven't used async functions before. If this means you, start part of this project early so you don't end up in a rush!**

- *For web languages like d3* Don't forget to run a local webserver when you're debugging.
See my a1 video or online tutorials for how to do this.
Being able to host a local webserver is an essential web development skill and very common in visualization design as well.

Readme Requirements
---

A good readme with screenshots and structured documentation is required for this project. 
It should be possible to scroll through your readme to get an overview of all the tools and visualizations you produced.

- Each visualization should start with a top-level heading (e.g. `# d3`)
- Each visualization should include a screenshot. Put these in an `img` folder and link through the readme (markdown command: `![caption](img/<imgname>)`.
- Write a paragraph for each visualization tool you use. What was easy? Difficult? Where could you see the tool being useful in the future? Did you have to use any hacks or data manipulation to get the right chart?

Other Requirements
---

0. Your code should be forked from the GitHub repo.
1. Place all code, Excel sheets, etcetera in a named folder. For example, `r-ggplot, matlab, mathematica, excel` and so on.
2. Your writeup (readme.md in the repo) should also contain the following:

- Description of the Technical achievements you attempted with this visualization.
  - Some ideas include interaction, such as mousing over to see more detail about the point selected.
- Description of the Design achievements you attempted with this visualization.
  - Some ideas include consistent color choice, font choice, element size (e.g. the size of the circles).

GitHub Details
---

- Fork the GitHub Repository. You now have a copy associated with your username.
- Make changes to fulfill the project requirements. 
- To submit, make a [Pull Request](https://help.github.com/articles/using-pull-requests/) on the original repository.

Grading
---

Grades on a 120 point scale. 
24 points will be based on your Technical and Design achievements, as explained in your readme. 

Make sure you include the files necessary to reproduce your plots.
You should structure these in folders if helpful.
We will choose some at random to run and test.

**NOTE: THE BELOW IS A SAMPLE ENTRY TO GET YOU STARTED ON YOUR README. YOU MAY DELETE THE ABOVE.**

# R + ggplot2 + R Markdown

R is a language primarily focused on statistical computing.
ggplot2 is a popular library for charting in R.
R Markdown is a document format that compiles to HTML or PDF and allows you to include the output of R code directly in the document.

To visualized the cars dataset, I made use of ggplot2's `geom_point()` layer, with aesthetics functions for the color and size.

While it takes time to find the correct documentation, these functions made the effort creating this chart minimal.


# d3...

(And so on...)


## Technical Achievements
- **Proved P=NP**: Using a combination of...
- **Solved AI Forever**: ...

### Design Achievements
- **Re-vamped Apple's Design Philosophy**: As demonstrated in my colorscheme...
