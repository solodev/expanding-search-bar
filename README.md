# expanding-search-bar
Often, headers are too crowded to offer a full search bar for users. Using this tutorial, you can make it so that a search bar appears on a specific link or event.


## Tutorial
For detailed instruction's, view Solodev's [How to Expand Your Site Search on Click](https://www.solodev.com/blog/web-design/how-to-expand-your-site-search-on-click.stml)

## Demo
Try out a working example on [JSFiddle](https://jsfiddle.net/solodev/be82nprc/).

## HTML
The tutorial contains the following basic HTML markup.

```
<header class="header position-relative">
  <div class="container">
    <div class="row align-items-center">
      <div class="col-lg-3 col-md-4 col-6 header--logo py-3">
        <a href=""><img src="https://raw.githubusercontent.com/solodev/expanding-search-bar/master/images/logo.png" class="img-fluid" alt=""></a>
      </div>
      <div class="header--menubar col-lg-9 offset-lg-0 col-md-3 offset-md-5  col-6 position-static">
        <div class="header--menu header--menu__top d-lg-flex d-none justify-content-right">
          <ul>
            <li><a href="">Blog</a></li>
            <li><a href="">Events</a></li>
            <li><a href="">Gallery</a></li>
            <li><a href="">News</a></li>
            <li class="header--search">Search <i class="fa fa-search"></i></li>
          </ul>
        </div>
        <div class="header--menu header--menu__bottom d-lg-flex d-none justify-content-right">
          <ul>
            <li class="menu-item-has-children"><a href="#">Community</a>
            </li>
            <li><a href="#">About</a></li>
            <li><a href="#">Products</a>
            </li>
            <li><a href="#">Contact</a></li>
            <li class="btn"><a href="#">I Want To</a></li>
          </ul>
        </div><!-- .menu-->

        <div class="header--search d-md-inline-block d-lg-none">
          <i class="fa fa-search"></i>
        </div>

        <div class="header--search_open">
          <div class="container">
            <form data-children-count="1">
              <span> <i class="fa fa-times" aria-hidden="true" alt="close search"></i></span>
              <input class="form-control" type="search" placeholder="How may we help you?">
              <button class="btn btn-search" type="submit"><i class="fa fa-search"></i></button>
            </form>
          </div>
        </div><!-- .header-search-open-->

        <button class="menu-hamburger d-md-inline-block d-lg-none">
          <i class="fas fa fa-bars"></i>
        </button>
      </div>
      <!--.header-menubar-->
    </div><!-- .row-->
  </div><!-- .container-->
</header>

<section class="hero hero--video">
  <img src="https://raw.githubusercontent.com/solodev/expanding-search-bar/master/images/hero-image.jpg" class="img-fluid">
</section><!-- .hero-->
```

## JS
```
 // search bar
 if ($(window).width() < 767) {
   $('.header .header--menubar').on('click', '.header--search', function(e) {
     $('.overlay').toggleClass('open');
   });
 } else {
   $('.header .header--menubar').on('click', '.header--search', function(e) {
     $('.header--search_open').toggleClass('open');
   });
 }

 $(document).mouseup(function(e) {
   var container = $('.header--menubar .header--search'),
     container2 = $('.header--search_open form');

   if (!container.is(e.target) && container.has(e.target).length === 0 && !container2.is(e.target) &&
     container2.has(e.target).length === 0) {
     $('.header--search_open').removeClass('open');
   }
 });

 $('.header--search_open form').on('click', 'span', function() {
   if ($(this).next().val() == '') {
     $('.header--search_open').removeClass('open');
   } else {
     $(this).next().val('')
   }
 })
```

## CSS
All required CSS is contained with style.css

## External Resources
This tutorial includes the following third party resources.

```
<!-- Bootstrap CSS -->
<link rel="stylesheet" href="https://stackpath.bootstrapcdn.com/bootstrap/4.4.1/css/bootstrap.min.css" integrity="sha384-Vkoo8x4CGsO3+Hhxv8T/Q5PaXtkKtu6ug5TOeNV6gBiFeWPGFN9MuhOf23Q9Ifjh" crossorigin="anonymous">
<!-- FontAwesome CSS -->
<link rel="stylesheet" href="https://stackpath.bootstrapcdn.com/font-awesome/4.7.0/css/font-awesome.css">
<!-- jQuery first, then Popper.js, then Bootstrap JS -->
<script src="https://code.jquery.com/jquery-3.4.1.slim.min.js" integrity="sha384-J6qa4849blE2+poT4WnyKhv5vZF5SrPo0iEjwBvKU7imGFAV0wwj1yYfoRSJoZ+n" crossorigin="anonymous"></script>
<script src="https://cdn.jsdelivr.net/npm/popper.js@1.16.0/dist/umd/popper.min.js" integrity="sha384-Q6E9RHvbIyZFJoft+2mJbHaEWldlvI9IOYy5n3zV9zzTtmI3UksdQRVvoxMfooAo" crossorigin="anonymous"></script>
<script src="https://stackpath.bootstrapcdn.com/bootstrap/4.4.1/js/bootstrap.min.js" integrity="sha384-wfSDF2E50Y2D1uUdj0O3uMBJnjuUD4Ih7YwaYd1iqfktj0Uod8GCExl3Og8ifwB6" crossorigin="anonymous"></script>
```