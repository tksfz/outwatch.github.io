---
title:  "Getting Started"
tags: chapters
---


First you will need to install Java and SBT if you haven't already.

Create a new SBT project and add the ScalaJS plugin to your `plugins.sbt`.
Then add the following line to your `build.sbt`.
{% highlight scala %}
libraryDependencies += "org.outwatch" %%% "outwatch" % "0.3.1"
{% endhighlight %}
Great, we've created our first OutWatch Project!

Now we'll create a small Hello World app to get you started.
First we'll create a new Scala file `HelloOutWatch.scala` in our main directory.
Inside we'll want to import the framework by specifying `import surge.dom._` at the top of our file.
We also need to import the Scala.js main class: `import scala.scalajs.js.JSApp`
Now we're ready to create our main entry point:
{% highlight scala %}
import scala.scalajs.js.JSApp
import surge.dom._

object HelloOutWatch extends JSApp {
  def main(): Unit = {

  }
}
{% endhighlight %}

Inside our `main` function we will want to write the following line:

{% highlight scala %}
OutWatch.render("#app", h1("Hello World"))
{% endhighlight %}

This will render an `h1` element into the element with the id `app`.

Next we'll need to create an `index.html` file at your project's root.
Inside we'll want to add a reference to our js files and also add a node in which we want to display our app:

{% highlight html %}
<body>
  <div id="app"></div>
  <script type="text/javascript" src="./target/scala-2.12/<your-project-name>-fastopt.js"></script>
  <script type="text/javascript" src="./target/scala-2.12/<your-project-name>-jsdeps.js"></script>
  <script type="text/javascript">
      HelloOutWatch().main();
  </script>
</body>
{% endhighlight %}

We're basically done here. We created our first app. Now we only need to run it.

To run this, simply launch `sbt` and then use the `fastOptJS` command to compile your code to JavaScript.
{% highlight text %}
$ sbt
> fastOptJS
{% endhighlight %}

And with that, we're done, check your browser, to see what we just created (it's not that special, but it's something).

### Recompiling your files as needed

Retyping `fastOptJS` every time we want to compile can get quite annoying and inefficient.
Luckily, in `sbt`, we can run every command in watch mode by simply adding a tilde `~` in front of it.
{% highlight text %}
$ sbt
> ~fastOptJS
[success] (...)
1. Waiting for source changes... (press enter to interrupt)
{% endhighlight %}


<h2 id="sbt-new">Using sbt new</h2>

The fastest way to create a new OutWatch application is by using `sbt new`.

{% highlight text %}
sbt new outwatch/seed.g8
{% endhighlight %}

This will create a prompt to create your first project.