---
title: Title
description: description

layout: generic
permalink: /contact

type: category

page-title: Контакты

---
<ul class="alt">
	<li><i class="fa fa-phone">&nbsp;</i><a href="tel:+7(495)123-45-67"><span itemprop="telephone">+7&nbsp;(495)&nbsp;123-45-67</span></a></li>
	<li><i class="fa fa-whatsapp">&nbsp;</i><a href="https://wa.me/74951234567"><span>Написать в WhatsApp</span></a></li>
	<li><i class="fa fa-envelope-o">&nbsp;</i><a href="mailto:info@veshi.ru"><span itemprop="email">info@veshi.ru</span></a></li>
	<li><div itemprop="address" itemscope itemtype="http://schema.org/PostalAddress"><i class="fa fa-map-marker">&nbsp;</i><span itemprop="postalCode">111222</span> г. <span itemprop="addressLocality">Москва</span>, <span itemprop="streetAddress">ул. Ленина, д. 5</span></div></li>
	<li><i class="fa fa-clock-o">&nbsp;</i><data itemprop="openingHours" value="Mo-Fri 10:00−20:00"> Пн-Пт, 10:00-19:00.</data></li>
</ul>
<div id='map'></div>
<script src='https://maps.googleapis.com/maps/api/js?key=AIzaSyDhVVXo6YEQbJaryZPqmx8g_SqMln8x8jY&extension=.js'></script> 
 
<script> 
	google.maps.event.addDomListener(window, 'load', init);
	var map;
	function init() {
		var mapOptions = {
			center: new google.maps.LatLng(55.477585,-322.682634),
			zoom: 10,
			zoomControl: true,
			zoomControlOptions: {
				style: google.maps.ZoomControlStyle.LARGE,
			},
			disableDoubleClickZoom: false,
			mapTypeControl: false,
			mapTypeControlOptions: {
				style: google.maps.MapTypeControlStyle.HORIZONTAL_BAR,
			},
			scaleControl: false,
			scrollwheel: false,
			panControl: false,
			streetViewControl: false,
			draggable : !('ontouchend' in document),
			overviewMapControl: false,
			overviewMapControlOptions: {
				opened: false,
			},
			mapTypeId: google.maps.MapTypeId.ROADMAP,
			styles: [{"featureType":"landscape","stylers":[{"saturation":-100},{"lightness":65},{"visibility":"on"}]},{"featureType":"poi","stylers":[{"saturation":-100},{"lightness":51},{"visibility":"simplified"}]},{"featureType":"road.highway","stylers":[{"saturation":-100},{"visibility":"simplified"}]},{"featureType":"road.arterial","stylers":[{"saturation":-100},{"lightness":30},{"visibility":"on"}]},{"featureType":"road.local","stylers":[{"saturation":-100},{"lightness":40},{"visibility":"on"}]},{"featureType":"transit","stylers":[{"saturation":-100},{"visibility":"simplified"}]},{"featureType":"administrative.province","stylers":[{"visibility":"off"}]},{"featureType":"water","elementType":"labels","stylers":[{"visibility":"on"},{"lightness":-25},{"saturation":-100}]},{"featureType":"water","elementType":"geometry","stylers":[{"hue":"#ffff00"},{"lightness":-25},{"saturation":-97}]}],
		}
		var mapElement = document.getElementById('map');
		var map = new google.maps.Map(mapElement, mapOptions);
		var locations = [
['А510', 'г. Москва, г. Троицк, ул. Физическая, д. 13', '+7(495)123-45-67', 'info@a510.ru', 'a510.ru', 55.464401, 37.29058599999996, '/images/solid-pin-black.png']
		];
		for (i = 0; i < locations.length; i++) {
			if (locations[i][1] =='undefined'){ description ='';} else { description = locations[i][1];}
			if (locations[i][2] =='undefined'){ telephone ='';} else { telephone = locations[i][2];}
			if (locations[i][3] =='undefined'){ email ='';} else { email = locations[i][3];}
		   if (locations[i][4] =='undefined'){ web ='';} else { web = locations[i][4];}
		   if (locations[i][7] =='undefined'){ markericon ='';} else { markericon = locations[i][7];}
			marker = new google.maps.Marker({
				icon: markericon,
				position: new google.maps.LatLng(locations[i][5], locations[i][6]),
				map: map,
				title: locations[i][0],
				desc: description,
				tel: telephone,
				email: email,
				web: web
			});
if (web.substring(0, 7) != "http://") {
link = "http://" + web;
} else {
link = web;
}
			bindInfoWindow(marker, map, locations[i][0], description, telephone, email, web, link);
	 }
 function bindInfoWindow(marker, map, title, desc, telephone, email, web, link) {
	  var infoWindowVisible = (function () {
			  var currentlyVisible = false;
			  return function (visible) {
				  if (visible !== undefined) {
					  currentlyVisible = visible;
				  }
				  return currentlyVisible;
			   };
		   }());
		   iw = new google.maps.InfoWindow();
		   google.maps.event.addListener(marker, 'click', function() {
			   if (infoWindowVisible()) {
				   iw.close();
				   infoWindowVisible(false);
			   } else {
				   var html= "<div style='color:#100e11;background-color:#fff;padding:5px;width:250px;'><h4>"+title+"</h4><p>"+desc+"<p><p>"+telephone+"<p><a href='mailto:"+email+"' >"+email+"<a><a href='"+link+"'' >"+web+"<a></div>";
				   iw = new google.maps.InfoWindow({content:html});
				   iw.open(map,marker);
				   infoWindowVisible(true);
			   }
		});
		google.maps.event.addListener(iw, 'closeclick', function () {
			infoWindowVisible(false);
		});
 }
}
</script>