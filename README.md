# reproducible-research-proj2
Reproducible Research Project 2

# Notes:

  * Found interesting information on ggplot usage on this page (in french): http://www.sthda.com/french/wiki/ggplot2-barplots-guide-de-demarrage-rapide-logiciel-r-et-visualisation-de-donnees
  * Some usefull R ggplot snippets:

```
# To remove a ggplot legend, one can use:
p+theme(legend.position="none")

# override the labels for a x axis:
p+scale_x_discrete(name="Event type 2", labels=focus_death$EVTYPE)

# To change the margin around a plot:
p<-p+theme(plot.background=element_rect(fill="darkseagreen"), plot.margin = unit(c(1, 1, 1, 1), "cm")) #top, right, bottom, left)

# Test for rendering bar plot with base plot system:
par(yaxt="n")
barplot(focus_death$total_death)
axis(1, at=seq(1, nfdeath, by=1), labels = FALSE)
text(x = seq(1, nfdeath, by=1), labels = focus_death$EVTYPE, srt = 90, pos = 1, xpd = TRUE)

# Additional code for focused datasets:
othdeath <- 100.0 - focus_death$accum_death[nfdeath]
othinj <- 100.0 - focus_inj$accum_injuries[nfinj]

focus_death <- rbind(focus_death, data.frame(EVTYPE = "others", total_death = othdeath, total_injuries = 0, accum_death = 100.0))
focus_inj <- rbind(focus_inj, data.frame(EVTYPE = "others", total_death = 0, total_injuries = othinj, accum_injuries = 100.0))

```

  * Additional infos on axes configurations: http://www.sthda.com/french/wiki/ggplot2-graduation-des-axes-guide-pour-personnaliser-les-etiquettes-des-graduations-logiciel-r-et-visualisation-de-donnees
  
  * To render multiple ggplot panels one could use the multiplot function defined on [this page](http://www.cookbook-r.com/Graphs/Multiple_graphs_on_one_page_(ggplot2)/) or as mentioned on [this page](http://stackoverflow.com/questions/24387376/r-weird-error-could-not-find-function-multiplot), we can use the arrange function from the **gridExtra** package.
  
  * Can also check [Beautiful plotting in R: a ggplot cheatsheet](http://zevross.com/blog/2014/08/04/beautiful-plotting-in-r-a-ggplot2-cheatsheet-3/)
