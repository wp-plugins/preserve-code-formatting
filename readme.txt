=== Preserve Code Formatting ===
Contributors: coffee2code
Donate link: http://coffee2code.com/donate
Tags: code, formatting, post body, content, display, writing, escape, coffee2code
Requires at least: 2.8
Tested up to: 3.0.1
Stable tag: 3.0
Version: 3.0

Preserve formatting of code for display by preventing its modification by WordPress and other plugins while retaining original whitespace and characters.


== Description ==

Preserve formatting of code for display by preventing its modification by WordPress and other plugins while retaining original whitespace and characters.

NOTE: Use of the visual text editor will pose problems as it can mangle your intent in terms of `<code>` tags.  I do not offer any support for those who have the visual editor active.

Notes:

Basically, you can just paste code into `<code>`, `<pre>`, and/or other tags you additionally specify and 
this plugin will:

* Prevent WordPress from HTML-encoding text (i.e. single- and double-quotes will not become curly; "--" and "---" will not become en dash and em dash, respectively; "..." will not become a horizontal ellipsis, etc)
* Prevent most other plugins from modifying preserved code
* Optionally preserve whitespace (in a variety of methods)
* Optionally preserve code added in comments

Keep these things in mind:

* ALL embedded HTML tags and HTML entities will be rendered as text to browsers, appearing exactly as you wrote them (including any `<br />`).
* By default this plugin filters 'the_content' (post content), 'the_excerpt' (post excerpt), and 'get_comment_text (comment content)'.

Example:
A post containing this within `<code></code>`:
`$wpdb->query("
        INSERT INTO $tablepostmeta
        (post_id,meta_key,meta_value)
        VALUES ('$post_id','link','$extended')
");`

Would, with this plugin enabled, look in a browser pretty much how it does above, instead of like:
`$wpdb->query(&#8212;
INSERT INTO $tablepostmeta
(post_id,meta_key,meta_value)
VALUES ('$post_id','link','$extended')
&#8213;);`


== Installation ==

1. Unzip `preserve-code-formatting.zip` inside the `/wp-content/plugins/` directory (or install via the built-in WordPress plugin installer)
1. Activate the plugin through the 'Plugins' admin menu in WordPress
1. Go to the `Settings` -> `Code Formatting` admin settings page (which you can also get to via the Settings link next to the plugin on the Manage Plugins page) and customize the settings.
1. Write a post with code contained within `<code>` and `</code>` tags (using the HTML editor, not the Visual editor).


== Frequently Asked Questions ==

= Why does my code still display all funky?  (by the way, I'm using the visual editor) =

The visual editor has a tendency to screw up some of your intent, especially when you are attempting to include raw code.  This plugin does not make any claims about working when you create posts with the visual editor enabled.


== Screenshots ==

1. A screenshot of the plugin's admin options page.


== Changelog ==

= 3.0 =
* Re-implementation by extending C2C_Plugin_016, which among other things adds support for:
    * Reset of options to default values
    * Better sanitization of input values
    * Offload of core/basic functionality to generic plugin framework
    * Additional hooks for various stages/places of plugin operation
    * Easier localization support
* Full localization support
* Change storing plugin instance in global variable to $c2c_preserve_code_formatting (instead of $preserve_code_formatting), to allow for external manipulation
* Rename class from 'PreserveCodeFormatting' to 'c2c_PreserveCodeFormatting'
* Remove docs from top of plugin file (all that and more are in readme.txt)
* Note compatibility with WP 2.9+, 3.0+
* Drop compatibility with versions of WP older than 2.8
* Add PHPDoc documentation
* Minor tweaks to code formatting (spacing)
* Add package info to top of plugin file
* Add Upgrade Notice section to readme.txt
* Update copyright date
* Remove trailing whitespace
* Add .pot file

= 2.5.4 =
* Fixed some borked code preservation by restoring some processing removed in previous release

= 2.5.3 =
* Fixed recently introduced bug affecting occasional code preservation by using a more robust alternative approach
* Fixed "Settings" link for plugin in plugin listing, which lead to blank settings page
* Changed help text for preservable tags settings input to be more explicit

= 2.5.2 =
* Fix to retain any attributes defined for tags being preserved
* Fixed recently introduced bug affecting occasional code preservation

= 2.5.1 =
* Fixed newly introduced bug that added unnecessary slashes to preserved code
* Fixed long-running bug where intended slashes in code got stripped on display (last remaining known bug)

= 2.5 =
* Fixed long-running bug that caused some preserved code to appear garbled
* Updated a lot of internal plugin management code
* Added 'Settings' link to plugin's plugin listing entry
* Used plugins_url() instead of hardcoded path
* Brought admin markup in line with modern conventions
* Minor reformatting (spacing)
* Noted compatibility through WP2.8+
* Dropped support for pre-WP2.6
* Updated copyright date
* Updated screenshot

= 2.0 =
* Completely rewritten
* Now properly handles code embedded in comments
* Created its own class to encapsulate plugin functionality
* Added admin options page under Options -> Code Formatting (or in WP 2.5: Settings -> Code Formatting). Options are now saved to database, negating need to customize code within the plugin source file.
* Removed function anti_wptexturize() as the new handling approach negates its need
* Changed description; updated installation instructions
* Added compatibility note
* Updated copyright date
* Moved into its own subdirectory; added readme.txt and screenshot
* Tested compatibility with WP 2.3.3 and 2.5

= 0.9 =
* Initial release


== Upgrade Notice ==

= 3.0 =
Recommended update. Highlights: re-implementation using custom plugin framework; full localization support; misc non-functionality documentation and formatting tweaks; renamed class; verified WP 3.0 compatibility; dropped support for versions of WP older than 2.8.