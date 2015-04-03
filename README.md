<!DOCTYPE html>
<html>
<head>
</head>
<body>
	<canvas id="c" width="500" height="500"></canvas>
	<script>
		var c = document.querySelector("#c");
		var ctx = c.getContext("2d");
		var img = new Image();
		img.src = "banner.JPG";
		ctx.drawImage(img, 0, 0, c.width, c.height);
		console.log(img);
		img.onload = function() {
          ctx.drawImage(this, 0, 0);
        };
		function greyConvert() {
			//var i = 0;
			var r;
			var g;
			var b;
			var avg;
			var imgData = ctx.getImageData(0, 0, c.width, c.height);
			for(var i = 0; i < imgData.data.length; i = i + 4) {
				r = imgData.data[i];
				g = imgData.data[i+1];
				b = imgData.data[i+2];
				avg = (r+g+b)/3;
				imgData.data[i] = avg;
				imgData.data[i+1] = avg;
				imgData.data[i+2] = avg;
			};
			console.log(imgData);

		};
		greyConvert();
		</script>
</body>
</html>
