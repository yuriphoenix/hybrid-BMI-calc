# hybrid-BMI-calc
a hybrid BMI calculator , which can be added to 
<html>
  <head>
    <title>BMI Calculator</title>
  </head>
  //The parametres, they will trigger the system to run the function when Something is entered.
  <p>Enter your weight: <input type="number" id="weight" oninput="Converter()" onchange="Converter()">
  <select type="multiple" id="weightunits" oninput="Converter()" onchange="Converter()">
        <option value="kg" selected="selected">kilograms</option>
        <option value="lb">pounds</option>
    </select>
  </p>
 
     <p>Enter your height: <input type="number" id="height" oninput="Converter()" onchange="Converter()">
    <select type="multiple" id="heightunits" oninput="Converter()" onchange="Converter()">
        <option value="metres" selected="selected">metres</option>
        <option value="inches">inches</option>
		 <option value="CM">CM</option>
		  <option value="feet">feet</option>
    </select></p>
	//the output feilds.
  <p>Your BMI Is: <span id="BMI"></span></p>
  <p>You Are: <span id="Health"></span></p>
  </html>
<script>
function Converter(){
/* This finds the inputs and  makes them  vars.*/
	var height= Number(document.getElementById("height").value);
	var heightunits=document.getElementById("heightunits").value;
	var weight =Number(document.getElementById("weight").value);
	var weightunits=document.getElementById("weightunits").value;

	/*I told the system that all calcs start with metres and kg, then / by the number of times that
	unit appears in a meter or kg to allow hybrid calcs.*/
	if (heightunits=="metres"){height}
	if (heightunits=="inches"){ height/=39}
	if (heightunits=="CM"){height/=100}
	if (heightunits=="feet"){height/=3.28}
	if (weightunits=="lb") {weight/=2.20462};
	if (weightunits=="kg") {weight};	
	
	/* The calc that allows for hybriding the weight and height. It appears to be very accruate but tsting has been limited*/
	var BMI = (weight / (height * height))
document.getElementById("BMI").innerText=Math.round(BMI * 100)/100;

/*Tells the system to workout the users bodytype based on the BMI result*/
var State =Math.round(BMI*100)/100;
if (State <18.5){
document.getElementById("Health").innerHTML ="Underweight";
}else{ if (State >=18.5 && State <=25){
document.getElementById("Health").innerHTML ="Healthy";
}else{ if (State >=25 && State <=30){
document.getElementById("Health").innerHTML ="Overweight";
}else{ if (State >30){
document.getElementById("Health").innerHTML ="Obese";
}}}};
};
</script>
