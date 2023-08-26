#include<REG51.H>			//Header file for 8051 microcontroller 
	
void T0Delay(void);  			//function prototype declaration

void main(void) 			// main function
{
	while(1)    			//repeat forever
	{
		P1=0xFF;   		//make high all bits of port 1
		T0Delay(); 		// call delay routine

		P1=0x00;   		// make low all bits of port 1
		T0Delay();  		// call delay routine
	}
}					//End of main 
void T0Delay()				//delay function
{
	TMOD=0x01;  			// use timer 0 , mode 1
					//Load value "FC" in timer 0 lower byte & load value "65" in timer 0 higher 					//byte for 1 second delay
	TL0=0xFC; 			// load TL0
	TH0=0x65;  			//load TH0
	TR0=1;      			// turn on Timer 0


while(TF0==0);  			//wait for TF0(timer 0 overflow flag) to roll over(overflow)
	TR0=0;   			//turn off timer 0 run control bit
	TF0=0; 				// clear timer 0 overflow flag bit.
}

