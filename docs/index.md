<h1><i class="fas fa-fire" style="color:#FA023C"></i> Cinder Theme <small>for MkDocs</small></h1>

## About

Cinder is a clean, responsive theme for static documentation sites that are generated with [MkDocs](https://github.com/mkdocs/mkdocs). It's built on the [Bootstrap 3 framework](https://getbootstrap.com/docs/3.3/) and includes pre-packaged:

<small><i class="fas fa-highlighter" style="color:#FA023C"></i> **[highlight.js v9.18.0](https://highlightjs.org/) syntax highlighting with support for [185 languages (over 30 by default) and over 90 styles](https://highlightjs.org/static/demo/)**</small></br>
<small><i class="fab fa-font-awesome-alt" style="color:#FA023C"></i> **[FontAwesome v5.12.0](https://fortawesome.github.io/Font-Awesome/) icon support**</small></br>
<small><i class="fas fa-font" style="color:#FA023C"></i> **[smashingly legible type scheme](./specimen#typography) to get your message out to your users**</small>

You are viewing the theme in action and can see a selection of the theme elements on the [Specimen page](./specimen/).

## Install

**<em>Required</em>**: Python 3.4+

### Install MkDocs & Create a New Project

If you haven't installed MkDocs yet, use the following command to install it:

<pre><code class="shell">$ pip install mkdocs</code></pre>

Next, navigate to a clean directory and create a new MkDocs project with the following command:

<pre><code class="shell">$ mkdocs new [projectname]</code></pre>

Replace `[projectname]` with the name of your project (without the brackets).

Then navigate to the root of your project directory:

<pre><code class="shell">$ cd [projectname]</code></pre>

### Install the Cinder Theme

Download the Cinder theme archive by clicking the button below.

<a href="https://github.com/chrissimpkins/cinder/archive/v1.2.0.zip"><button type="button" class="btn btn-success"><i class="fas fa-cloud-download-alt fa-3x"></i> </br> <span style="font-size:20px;">Download Cinder</span></button></a>

Unpack the contents of the archive into a directory named `cinder` at the top level of your MkDocs project directory.

Your project directory should now look like this:

<pre><code class="shell">.
├── mkdocs.yml
├── cinder
│     ├── css
│     ├── img
│     ├── js
│     ├── base.html
│     ├── content.html
│     ├── 404.html
│     ├── nav-sub.html
│     ├── nav.html
│     └── toc.html
└── docs
      └── index.md
</code></pre>

MkDocs projects use a YAML settings file called `mkdocs.yml`. This is located in the root of your project directory after you use the `mkdocs new` command. Open the file in a text editor and modify it to include the `theme` settings as follows:

<pre><code class="yaml">site_name: [YOURPROJECT]
theme:
  name: null
  custom_dir: 'cinder'
nav:
  - Home: index.md</code></pre>

See the [MkDocs documentation](https://www.mkdocs.org/user-guide/custom-themes/#creating-a-custom-theme) for additional details.

<div class="bs-callout bs-callout-default">
  <h4>Updates, the Manual Approach</h4>
  If you choose the manual install approach, you can update your Cinder theme by downloading the new cinder.zip release archive and including it in your project. Then re-build your static site files (see instructions below).
</div>

## Test with a Local Site Server

Use the following command to establish a local server for your site:

<pre><code class="shell">$ mkdocs serve</code></pre>

Then open your site in any browser at the URL `http://localhost:8000`.

## Create Your Site

### Add Content with Markdown Syntax

Get to work on your site home page by opening the `docs/index.md` file and editing it in Markdown syntax. The HTML automatically updates in the browser when you save the Markdown file if you use the MkDocs server (see command above).

### Add New Pages

Add new pages to your site by creating a new Markdown file in your `docs` directory, then linking to the new page in the `mkdocs.yml` file. This uses a `Page Name : Markdown file` syntax.

For example, to add an About page using a Markdown file that is located on the path `docs/about.md`, you would format the `mkdocs.yml` file as follows:

<pre><code class="yaml">site_name: [YOURPROJECT]
theme:
  name: null
  custom_dir: 'cinder'
nav:
  - Home: index.md
  - About: about.md</code></pre>

Add additional pages to your site by repeating the above series of steps.

## Build Your Site

Build your site files with the command:

<pre><code class="shell">$ mkdocs build</code></pre>

Your site files are built in the `site` directory and are ready to use. Deploy the contents of the `site` directory to your web server.

## Important Configuration Issues

<div class="bs-callout bs-callout-warning">
  <h4><i class="fas fa-exclamation-triangle"></i> Please review these issues before you push your site into a production setting!</h4>
</div>

### 1. Set the `site_url` configuration field

You must set the `site_url` field in your `mkdocs.yml` file to the appropriate production URL in order to generate a valid `sitemap.xml` file ([issue #80](https://github.com/chrissimpkins/cinder/issues/80)).

Here is an example from the [Cinder project `mkdocs.yml` file](https://github.com/chrissimpkins/cinder/blob/master/mkdocs.yml):

```yml
site_name: Cinder
site_url: https://sourcefoundry.org/cinder/
site_author: Christopher Simpkins
site_description: "A clean, responsive theme for static documentation websites that are generated with MkDocs"
repo_url: "https://github.com/chrissimpkins/cinder"
copyright: "Cinder is licensed under the <a href='https://github.com/chrissimpkins/cinder/blob/master/LICENSE.md'>MIT license</a>"

theme:
  name: null
  custom_dir: cinder
  colorscheme: github
  highlightjs: true
  hljs_languages:
    - yaml

nav:
  - Home: index.md
  - Specimen: specimen.md

markdown_extensions:
  - admonition
```

The `sitemap.xml` file will be located at `[SITE_URL]/sitemap.xml` when you push your site into the production environment. During development the `sitemap.xml` file can be found at `http://127.0.0.1:8000/sitemap.xml`.

## Site Customization

The following are a few common customizations that you might be interested in. For much more detail about the configuration of your site, check out the [MkDocs Configuration documentation](https://github.com/mkdocs/mkdocs/blob/master/docs/user-guide/configuration.md).

### Syntax Highlighting Color Scheme

Cinder supports the [90+ highlightjs color schemes](https://highlightjs.org/static/demo/). The `github` color scheme that you see on this page is the default and will be used if you do not specify otherwise.

To change to a different scheme, include the `colorscheme` field under the `theme` field in your `mkdocs.yml` file and enter the color scheme name. For example, to switch to the [Dracula theme](https://draculatheme.com/), enter the following:

```yml
theme:
  name: null
  custom_dir: cinder
  colorscheme: dracula
```

and then rebuild your site.

The color scheme name should match the base name of the highlightjs CSS file. See the [`src/styles` directory of the highlightjs repository](https://github.com/highlightjs/highlight.js/tree/master/src/styles) for a complete list of these CSS paths.

### Syntax Highlighting Language Support

By default, Cinder supports the ~30 syntaxes listed under `common` in [the documentation](https://highlightjs.org/static/demo/). You can broaden support to any of the over 130 highlightjs languages using definitions in your `mkdocs.yml` file.

To add a new language, create a list of additional languages as a `hljs_languages` sub-field under the `theme` field in the `mkdocs.yml` file. The definitions are formatted as a newline-delimited list with `-` characters.

For example, to add support for the Julia and Perl languages, format your configuration file like this:

```yml
theme:
  name: null
  custom_dir: cinder
  hljs_languages:
    - julia
    - perl
```

Use the base file name of the [JavaScript files located in the CDN](https://cdn.jsdelivr.net/gh/highlightjs/cdn-release@9.18.0/build/languages/) for your syntax definitions.

### Site Favicon

Create an `img` subdirectory in your `docs` directory and add a custom favicon.ico file. See the [MkDocs documentation](https://www.mkdocs.org/#changing-the-favicon-icon) for additional details.

### Add Your Own CSS Stylesheets

Create a `css` directory inside your `docs` directory and add your CSS files. You can overwrite any of the Cinder styles in your CSS files. Then include your CSS files in the `mkdocs.yml` file with the `extra_css` field:

<pre><code class="yaml">site_name: [YOURPROJECT]
theme: cinder
extra_css:
  - "css/mystyle.css"
  - "css/myotherstyle.css"
nav:
  - Home: index.md
  - About: about.md</code></pre>

Your CSS styles fall at the end of the cascade and will override all styles included in the theme (including Bootstrap and default Cinder styles). You can find the Cinder and Bootstrap CSS files on the paths `cinder/css/cinder.css` and `cinder/css/bootstrap.min.css`, respectively.

### Add Your Own JavaScript

Create a `js` directory inside your `docs` directory and add your JS files. Then include your JS files in the `mkdocs.yml` file with the `extra_js` field:

<pre><code class="yaml">site_name: [YOURPROJECT]
theme: cinder
extra_js:
  - "js/myscript.js"
  - "js/myotherscript.js"
nav:
  - Home: index.md
  - About: about.md</code></pre>

### Keyboard shortcuts

Place the following in your `mkdocs.yml` file to enable keyboard shortcuts:

```shell
shortcuts:
    help: 191    # ?
    next: 39     # right arrow
    previous: 37 # left arrow
    search: 83   # s
```

The numbers correspond to the key that you would like to use for that shortcut. You can use [https://keycode.info/](https://keycode.info/) to find the keycode you want.

### Extending Cinder

Create a new directory within your project (e.g., `cinder-theme-ext/`) and create `main.html`. Add the following line at the top of the HTML file.

```html
{% extends "base.html" %}
```

Instead of using `theme_dir: cinder` in `mkdocs.yml`, use:

<pre><code class="yaml">theme:
    name: cinder
    custom_dir: [custom dir]</code></pre>

Refer to [MkDocs Documentation - Using the theme custom_dir](https://www.mkdocs.org/user-guide/styling-your-docs/#using-the-theme-custom_dir) for more information.

Use the following examples as reference. You can put your own [Jinja2](http://jinja.pocoo.org/) within the blocks. More information can be found in [MkDocs Documentation - Overriding Template Blocks](https://www.mkdocs.org/user-guide/styling-your-docs/#overriding-template-blocks).

#### Adding extra HTML to the head tag

Append to `main.html`:

```html
{% block extrahead %}
<meta name="author" content="{{ page.meta.author }}" />
{% endblock %}
```

#### Replacing footer

Append to `main.html`:

```html
{% block footer %}
<hr />
<p>
  {% if config.copyright %}
  <small>{{ config.copyright }}<br /></small>
  {% endif %}
  <small
    >Documentation built with
    <a href="http://www.mkdocs.org/">MkDocs</a>.</small
  >
  {% if page.meta.revision_date %}
  <small><br /><i>Updated {{ page.meta.revision_date }}</i></small>
  {% endif %}
</p>
{% endblock %}
```

`page.meta.revision_date` can be set by using [meta-data (front-matter)](https://www.mkdocs.org/user-guide/writing-your-docs/#meta-data) at the beginning of your Markdown document or using [mkdocs-git-revision-date-plugin](https://github.com/zhaoterryy/mkdocs-git-revision-date-plugin).

### Github or Bitbucket Repository Link

Include the `repo_url` field and define it with your repository URL:

<pre><code class="yaml">site_name: [YOURPROJECT]
theme: cinder
repo_url: "https://github.com/chrissimpkins/cinder"
nav:
  - Home: index.md
  - About: about.md</code></pre>

The link appears at the upper right hand corner of your site.

### License Declaration and Link

The Cinder theme displays your license declaration in the footer if you include a `copyright` field and define it with the text (and optionally the HTML link) that you would like to display:

<pre><code class="yaml">site_name: [YOURPROJECT]
theme: cinder
copyright: "Cinder is licensed under the &lt;a href='https://github.com/chrissimpkins/cinder/blob/master/LICENSE.md'&gt;MIT license</a>"
nav:
  - Home: index.md
  - About: about.md</code></pre>

### Disabling Theme Features

The Cinder theme can turn off some theme features entirely in `mkdocs.yml`, for situations where you don't need these features. If this is all the customization required, it saves overriding theme files. For example:

```yml
theme:
  name: cinder
  # Turn off Previous/Next navigation links in the navbar
  disable_nav_previous_next: true
  # Turn off Search in the navbar
  disable_nav_search: true
  # Turn off the site_name link in the navbar
  disable_nav_site_name: true
  # Turn off the footer entirely
  disable_footer: true
  # Turn off the default footer message, but display the page revision date if it's available
  disable_footer_except_revision: true
```

## Issues

If you have any issues with the theme, please report them on the Cinder repository:

<a href="https://github.com/chrissimpkins/cinder/issues/new"><button class="btn btn-primary btn-lg" type="submit"><i class="fab fa-github fa-2x"></i> Report Issue</button></a>
<a href="https://github.com/chrissimpkins/cinder/issues"><button class="btn btn-primary btn-lg" type="submit"> Active Issues <i class="fab fa-github fa-2x"></i></button></a>

## License

Cinder is licensed under the [MIT license](https://github.com/chrissimpkins/cinder/blob/master/LICENSE.md).

<h1>Cinder Theme Specimen</h1>

## Typography

### Typefaces

- Headers: [Inter](https://github.com/rsms/inter)
- Body: [Open Sans](https://www.google.com/fonts/specimen/Open+Sans)
- Code: [Hack](http://sourcefoundry.org/hack/)

### Body Copy

You think water moves fast? You should see ice. <strong>It moves like it has a mind</strong>. Like it knows it killed the world once and got a taste for murder. <em>After the avalanche, it took us a week to climb out</em>. Now, I don't know exactly when we turned on each other, but I know that seven of us survived the slide... and only five made it out.

Now we took an oath, that I'm breaking now. [We said](#) we'd say it was the snow that killed the other two, but it wasn't. Nature is lethal but it doesn't hold a candle to man.

Like inline code? Here is a string for you <code>010101010</code>.

### Lead Body Copy

<p class="lead">Vivamus sagittis lacus vel augue laoreet rutrum faucibus dolor auctor. Duis mollis, est non commodo luctus.</p>

### Headings

All HTML headings, `<h1>` through `<h6>`, are available. `.h1` through `.h6` classes are also available, for when you want to match the font styling of a heading but still want your text to be displayed inline.

<h1>h1. Heading</h1>
<h2>h2. Heading</h2>
<h3>h3. Heading</h3>
<h4>h4. Heading</h4>
<h5>h5. Heading</h5>
<h6>h6. Heading</h6>

<h1>h1. Heading <small>Secondary text</small></h1>
<h2>h2. Heading <small>Secondary text</small></h2>
<h3>h3. Heading <small>Secondary text</small></h3>
<h4>h4. Heading <small>Secondary text</small></h4>
<h5>h5. Heading <small>Secondary text</small></h5>
<h6>h6. Heading <small>Secondary text</small></h6>

### Blockquotes

<blockquote>
  <p>Lorem ipsum dolor sit amet, consectetur adipiscing elit. Integer posuere erat a ante.</p>
  <footer>Someone famous in <cite title="Source Title">Source Title</cite></footer>
</blockquote>

### Lists

- `mkdocs new [dir-name]` - Create a new project.
- `mkdocs serve` - Start the live-reloading docs server.
- `mkdocs build` - Build the documentation site.
- `mkdocs help` - Print this help message.

### Horizontal Description Lists

<dl class="dl-horizontal">
  <dt>Something</dt>
  <dd>This is something</dd>
  <dt>SomethingElse</dt>
  <dd>This is something else</dd>
</dl>

### Contextual Colors

<p class="text-muted">Lorem ipsum dolor sit amet, consectetur adipiscing elit. Integer posuere erat a ante.</p>
<p class="text-primary">Lorem ipsum dolor sit amet, consectetur adipiscing elit. Integer posuere erat a ante.</p>
<p class="text-success">Lorem ipsum dolor sit amet, consectetur adipiscing elit. Integer posuere erat a ante.</p>
<p class="text-info">Lorem ipsum dolor sit amet, consectetur adipiscing elit. Integer posuere erat a ante.</p>
<p class="text-warning">Lorem ipsum dolor sit amet, consectetur adipiscing elit. Integer posuere erat a ante.</p>
<p class="text-danger">Lorem ipsum dolor sit amet, consectetur adipiscing elit. Integer posuere erat a ante.</p>

## Code

### Inline Code

This is an example of inline code `#import requests`

<h3>Preformatted Code Blocks <small>with Syntax Highlighting</small></h3>

<pre><code class="python">def request(method, url, **kwargs):
    """Constructs and sends a :class:`Request <Request>`.
    Usage::
      >>> import requests
      >>> req = requests.request('GET', 'https://httpbin.org/get')
      <Response [200]>
    """

    # By using the 'with' statement we are sure the session is closed, thus we
    # avoid leaving sockets open which can trigger a ResourceWarning in some
    # cases, and look like a memory leak in others.
    with sessions.Session() as session:
        return session.request(method=method, url=url, **kwargs)

def get(url, params=None, **kwargs):
    r"""Sends a GET request.
    :param url: URL for the new :class:`Request` object.
    :param params: (optional) Dictionary, list of tuples or bytes to send
        in the body of the :class:`Request`.
    :param \*\*kwargs: Optional arguments that ``request`` takes.
    :return: :class:`Response <Response>` object
    :rtype: requests.Response
    """

    kwargs.setdefault('allow_redirects', True)
    return request('get', url, params=params, **kwargs)
</code></pre>

<div id="language-support"></div>

<small>(Source code sample from the Python <a href="https://github.com/requests/requests">requests library</a>, <a href="https://github.com/requests/requests/blob/master/LICENSE">Apache License, v2.0</a>)</small>

Syntax highlighting support is available for and of the following languages listed on the <a href="https://highlightjs.org/download/">highlightjs website</a>. See the <a href="https://www.mkdocs.org/user-guide/styling-your-docs/">mkdocs "styling your docs"</a> hljs_languages section for info on how to load languages dynamically.

<div class="bs-callout bs-callout-info">
  <h4>Note</h4>
  Include source code formatted in <a href="https://github.github.com/gfm/#fenced-code-blocks" class="alert-link">Github-flavored Markdown fenced code blocks</a> with an <a href="https://github.github.com/gfm/#info-string" class="alert-link">info string</a> that defines the supported programming language to automate syntax highlighting when your site is built.
</div>

## Tables

### Striped Table

<table class="table table-striped">
  <thead>
	  <tr>
	  	<th>#</th>
	  	<th>Head 1</th>
	  	<th>Head 2</th>
	  	<th>Head 3</th>
	  </tr>
	  </thead>
	  <tbody>
	  <tr>
	  	<th scope="row">1</th>
	  	<td>Box 1</td>
	  	<td>Box 2</td>
	  	<td>Box 3</td>
	  </tr>
	    <tr>
	    <th scope="row">2</th>
	  	<td>Box 4</td>
	  	<td>Box 5</td>
	  	<td>Box 6</td>
	  </tr>
	  <tr>
	    <th scope="row">3</th>
	  	<td>Box 7</td>
	  	<td>Box 8</td>
	  	<td>Box 9</td>
	  </tr>
  </tbody>
</table>

### Bordered Table

<table class="table table-bordered">
  <thead>
	  <tr>
	  	<th>#</th>
	  	<th>Head 1</th>
	  	<th>Head 2</th>
	  	<th>Head 3</th>
	  </tr>
	  </thead>
	  <tbody>
	  <tr>
	  	<th scope="row">1</th>
	  	<td>Box 1</td>
	  	<td>Box 2</td>
	  	<td>Box 3</td>
	  </tr>
	    <tr>
	    <th scope="row">2</th>
	  	<td>Box 4</td>
	  	<td>Box 5</td>
	  	<td>Box 6</td>
	  </tr>
	  <tr>
	    <th scope="row">3</th>
	  	<td>Box 7</td>
	  	<td>Box 8</td>
	  	<td>Box 9</td>
	  </tr>
  </tbody>
</table>

## Buttons

### Default Buttons

<a class="btn btn-default" href="#" role="button">Link</a>
<button class="btn btn-default" type="submit">Button</button>
<input class="btn btn-default" type="button" value="Input">
<input class="btn btn-default" type="submit" value="Submit">

### Styled Buttons

<!-- Standard button -->

<button type="button" class="btn btn-default">Default</button>

<!-- Provides extra visual weight and identifies the primary action in a set of buttons -->

<button type="button" class="btn btn-primary">Primary</button>

<!-- Indicates a successful or positive action -->

<button type="button" class="btn btn-success">Success</button>

<!-- Contextual button for informational alert messages -->

<button type="button" class="btn btn-info">Info</button>

<!-- Indicates caution should be taken with this action -->

<button type="button" class="btn btn-warning">Warning</button>

<!-- Indicates a dangerous or potentially negative action -->

<button type="button" class="btn btn-danger">Danger</button>

### Button Sizes

<p>
  <button type="button" class="btn btn-primary btn-lg">Large button</button>
  <button type="button" class="btn btn-default btn-lg">Large button</button>
</p>
<p>
  <button type="button" class="btn btn-primary">Default button</button>
  <button type="button" class="btn btn-default">Default button</button>
</p>
<p>
  <button type="button" class="btn btn-primary btn-sm">Small button</button>
  <button type="button" class="btn btn-default btn-sm">Small button</button>
</p>
<p>
  <button type="button" class="btn btn-primary btn-xs">Extra small button</button>
  <button type="button" class="btn btn-default btn-xs">Extra small button</button>
</p>

### Block Level Buttons

<button type="button" class="btn btn-primary btn-lg btn-block">Block level button</button>
<button type="button" class="btn btn-default btn-lg btn-block">Block level button</button>

## Alerts

<div class="alert alert-primary" role="alert">
  A simple primary alert—check it out!
</div>
<div class="alert alert-secondary" role="alert">
  A simple secondary alert—check it out!
</div>
<div class="alert alert-success" role="alert">
  A simple success alert—check it out!
</div>
<div class="alert alert-danger" role="alert">
  A simple danger alert—check it out!
</div>
<div class="alert alert-warning" role="alert">
  A simple warning alert—check it out!
</div>
<div class="alert alert-info" role="alert">
  A simple info alert—check it out!
</div>
<div class="alert alert-light" role="alert">
  A simple light alert—check it out!
</div>
<div class="alert alert-dark" role="alert">
  A simple dark alert—check it out!
</div>

## Callouts

<div class="bs-callout bs-callout-default">
  <h4>Default Callout</h4>
  This is a default callout.
</div>

<div class="bs-callout bs-callout-primary">
  <h4>Primary Callout</h4>
  This is a primary callout.
</div>

<div class="bs-callout bs-callout-success">
  <h4>Success Callout</h4>
  This is a success callout.
</div>

<div class="bs-callout bs-callout-info">
  <h4>Info Callout</h4>
  This is an info callout.
</div>

<div class="bs-callout bs-callout-warning">
  <h4>Warning Callout</h4>
  This is a warning callout.
</div>

<div class="bs-callout bs-callout-danger">
  <h4>Danger Callout</h4>
  This is a danger callout.
</div>

## Admonitions

The following admonitions are formatted like the callouts above but can be implemented in Markdown when you include the `admonition` Markdown extension in your `mkdocs.yml` file.

Add the following setting to `mkdocs.yml`:

```yaml
markdown_extensions:
  - admonition
```

and then follow the instructions in [the extension documentation](https://python-markdown.github.io/extensions/admonition/) to author admonitions in your documentation.

Cinder currently supports `note`, `warning`, and `danger` admonition types.

!!! note
Lorem ipsum dolor sit amet, consectetur adipiscing elit. Nulla et euismod
nulla. Curabitur feugiat, tortor non consequat finibus, justo purus auctor
massa, nec semper lorem quam in massa.

    <pre><code>
    \# this is a note
    def func(arg) {
      \# notable things are in here!
      return None
    }
    </code></pre>

!!! warning
Lorem ipsum dolor sit amet, consectetur adipiscing elit. Nulla et euismod
nulla. Curabitur feugiat, tortor non consequat finibus, justo purus auctor
massa, nec semper lorem quam in massa.

    <pre><code>
    \# this is a warning
    def func(arg) {
      \# be careful!
      return None
    }
    </code></pre>

!!! danger
Lorem ipsum dolor sit amet, consectetur adipiscing elit. Nulla et euismod
nulla. Curabitur feugiat, tortor non consequat finibus, justo purus auctor
massa, nec semper lorem quam in massa.

    <pre><code>
    \# this is dangerous
    def func(arg) {
      \# BOOM!
      return None
    }
    </code></pre>
