function start(){
  getUserLocation();
  // GetMap();
  
}

window.onload  = start;

var map = null;
var searchManager = null;
var currInfobox = null;
var lat = 17.6;
var longi = 56.6;



function getUserLocation(){
  // var geoLocationProvider = new Microsoft.Maps.GeoLocationProvider(map);
  //alert("here");
  try
  {
    //alert('Error getting location');
    navigator.geolocation.getCurrentPosition(
      function(position){

        lat = position.coords.latitude;
        longi = position.coords.longitude;
        // alert(lat);
        // alert(longi);
        setTimeout(function(){
          GetMap();
        }, 3000);
      },
      function(){
        alert('Error getting location');
      });
  }
  catch(e)
  {
    alert(e);
  } 
}

function GetMap(){
   Microsoft.Maps.loadModule('Microsoft.Maps.Themes.BingTheme', { callback: function() 
       {
           map = new  Microsoft.Maps.Map(document.getElementById('divMap'), 
           { 
              credentials: "AncDAyCFAhw1FD9JOVrRLEltvp2iZq1U19oLHwR5QMInBi3gtBUgv1ko93vW5dFW",
              mapTypeId:  Microsoft.Maps.MapTypeId.road,
              enableClickableLogo: false,
              enableSearchLogo: false,
              center: new  Microsoft.Maps.Location(lat, longi),
              zoom: 15,
              theme: new  Microsoft.Maps.Themes.BingTheme()
           }); 
           map.entities.clear(); 
           var pushpinOptions = {icon: 'http://wcdn1.dataknet.com/static/resources/icons/set29/9ee6493d.png', width: 50, height: 50}; 
           var pushpin= new Microsoft.Maps.Pushpin(map.getCenter(), pushpinOptions); 
           map.entities.push(pushpin);

           var pushpinOptions = {icon: 'https://raw.githubusercontent.com/d-cent/patterns/master/source/assets/img/favicon.png',  draggable: true}; 
           var pushpin= new Microsoft.Maps.Pushpin(map.getCenter(), pushpinOptions); 
           map.entities.push(pushpin); 
           
          
       }
    });
}

   
function createSearchManager() {
   map.addComponent('searchManager', new  Microsoft.Maps.Search.SearchManager(map));
   searchManager = map.getComponent('searchManager');
}


function LoadSearchModule1() {
   Microsoft.Maps.loadModule('Microsoft.Maps.Search', {  callback: searchRequest1 })
}
function LoadSearchModule2() {
   Microsoft.Maps.loadModule('Microsoft.Maps.Search', {  callback: searchRequest2 })
}
function LoadSearchModule3() {
   Microsoft.Maps.loadModule('Microsoft.Maps.Search', {  callback: searchRequest3 })
}



function searchRequest1() {
   createSearchManager();
   var query = 'restrooms'; //document.getElementById('txtSearch').value;
   var request =
       {
           query: query,
           count: 20,
           startIndex: 0,
           bounds: map.getBounds(),
           callback: search_onSearchSuccess,
           errorCallback:  search_onSearchFailure
       };
   searchManager.search(request);
           var pushpinOptions = {icon: 'http://wcdn1.dataknet.com/static/resources/icons/set29/9ee6493d.png', width: 50, height: 50}; 
           var pushpin= new Microsoft.Maps.Pushpin(map.getCenter(), pushpinOptions); 
           map.entities.push(pushpin);

           var pushpinOptions = {icon: 'https://raw.githubusercontent.com/d-cent/patterns/master/source/assets/img/favicon.png',  draggable: true}; 
           var pushpin= new Microsoft.Maps.Pushpin(map.getCenter(), pushpinOptions); 
           map.entities.push(pushpin); 
 
 }

 function searchRequest2() {
   createSearchManager();
   var query = 'dustbins'; //document.getElementById('txtSearch').value;
   var request =
       {
           query: query,
           count: 20,
           startIndex: 0,
           bounds: map.getBounds(),
           callback: search_onSearchSuccess,
           errorCallback:  search_onSearchFailure
       };
   searchManager.search(request);
           var pushpinOptions = {icon: 'http://wcdn1.dataknet.com/static/resources/icons/set29/9ee6493d.png', width: 50, height: 50}; 
           var pushpin= new Microsoft.Maps.Pushpin(map.getCenter(), pushpinOptions); 
           map.entities.push(pushpin);

           var pushpinOptions = {icon: 'https://raw.githubusercontent.com/d-cent/patterns/master/source/assets/img/favicon.png',  draggable: true}; 
           var pushpin= new Microsoft.Maps.Pushpin(map.getCenter(), pushpinOptions); 
           map.entities.push(pushpin); 
 
 }

  function searchRequest3() {
   createSearchManager();
   var query = 'supermarket'; //document.getElementById('txtSearch').value;
   var request =
       {
           query: query,
           count: 20,
           startIndex: 0,
           bounds: map.getBounds(),
           callback: search_onSearchSuccess,
           errorCallback:  search_onSearchFailure
       };
   searchManager.search(request);
           var pushpinOptions = {icon: 'http://wcdn1.dataknet.com/static/resources/icons/set29/9ee6493d.png', width: 50, height: 50}; 
           var pushpin= new Microsoft.Maps.Pushpin(map.getCenter(), pushpinOptions); 
           map.entities.push(pushpin);

           var pushpinOptions = {icon: 'https://raw.githubusercontent.com/d-cent/patterns/master/source/assets/img/favicon.png',  draggable: true}; 
           var pushpin= new Microsoft.Maps.Pushpin(map.getCenter(), pushpinOptions); 
           map.entities.push(pushpin); 
 
 }



function search_onSearchSuccess(result, userData) {
   map.entities.clear();
        

   var searchResults = result && result.searchResults;
   if (searchResults[0]) { 
          //alert("here");
          var pushpinOptions = {icon: 'https://maps.gstatic.com/mapfiles/ms2/micons/ltblue-dot.png', width: 30, height: 50};
            var pushpin = new Microsoft.Maps.Pushpin(searchResults[0].location, pushpinOptions); 

            map.setView({ center: searchResults[0].location, zoom: 15 }); 
            map.entities.push(pushpin); 
        } 
   if (searchResults) {
       for (var i = 1; i < searchResults.length; i++) {
           search_createMapPin(searchResults[i]);
       }
       if (result.searchRegion &&  result.searchRegion.mapBounds) {
           map.setView({ center: searchResults[0].location, zoom: 20,  bounds:  result.searchRegion.mapBounds.locationRect });
       }
       else {
           alert('No results');
       }
    }
}

function search_createMapPin(result) {
   if (result) {
       var pin = new Microsoft.Maps.Pushpin(result.location, null);
       Microsoft.Maps.Events.addHandler(pin, 'click', function () {  
  search_showInfoBox(result) });
       map.entities.push(pin);
   }
}

function search_showInfoBox(result) {
   if (currInfobox) {
   currInfobox.setOptions({ visible: true });
   map.entities.remove(currInfobox);
   }
   currInfobox = new Microsoft.Maps.Infobox(
       result.location,
       {
           title: result.name,
           description: [result.address,  result.city, result.state, 
             result.country,  result.phone].join(' '),
           showPointer: true,
           titleAction: null,
           titleClickHandler: null 
       });
   currInfobox.setOptions({ visible: true });
   map.entities.push(currInfobox);
}

function search_onSearchFailure(result, userData) {
   alert('Search  failed');
}
